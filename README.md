@Configuration
@EnableReactiveMongoRepositories
public class ReactiveMongoConfig extends AbstractReactiveMongoConfiguration {

    @Value("${spring.data.mongodb.host:localhost}")
    private String host;

    @Value("${spring.data.mongodb.port:27017}")
    private int port;

    @Value("${spring.data.mongodb.database}")
    private String database;

    @Value("${spring.data.mongodb.username}")
    private String username;

    @Value("${spring.data.mongodb.password}")
    private String password;

    @Override
    protected String getDatabaseName() {
        return database;
    }

    @Override
    public MongoClient reactiveMongoClient() {
        MongoCredential credential = MongoCredential.createCredential(
            username, 
            "admin", // authentication database
            password.toCharArray()
        );

        return MongoClients.create(
            MongoClientSettings.builder()
                .applyToClusterSettings(builder -> 
                    builder.hosts(Arrays.asList(new ServerAddress(host, port))))
                .credential(credential)
                .build()
        );
    }
}