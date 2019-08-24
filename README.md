### ribbon
---
https://github.com/Netflix/ribbon

```java
HttpResourceGroup httpResourceGroup = Ribbon.createHttpResourceGroup("movieServiceClient",
  ClientOptions.create()
    .withMaxAutoRetiesNexServer(3)
    .withConfigurationBasedServerList("localhost:8080,localhost:8088"));
HttpRequestTemplate<ByteBuf> recommendationsByUserIdTemplate = httpRsourceGroup.newTemplateBuilder("recommendationsByUserId", ByteBuf.class)
  .withMethod("GET")
  .withUriTemplate(0
  .withFallbackProvider()
  .withResponseValidator()
  .build();
Observable<ByteBuf> result = recommendationsByUserIdTemplate.requestBuilder()
  .withRequestProperty("userId", "user1")
  .build()
  .observe();
  
public interface MovieService {
   @Http(
     method = HttpMethod.GET,
     uri = "/users/{userId}/recommendations",)
   RibbonRequest<ByteBuf> recommendationsByUserId(@Var("userId") String userId);
}

MovieService movieService = Ribbon.from(MovieService.class);
Observable<ByteBuf> result = movieService.recommendationsByUserId("user1").observe();

IRule rule = new AvailabilityFilteringRule();
ServerList<DiscoveryEnabledServer> list = new DiscoveryEnalbedNIWSServerList("MyVIP:7001");
ServerListFilter<DiscoveryEnabledServer> filter = new ZoneAffinityServerListFilter<>();
ZoneAwareLoadBalancer<DiscoveryEnabledServer> lb = LoadBalanceBuilder.<DiscovertyEnabledServer>newBuilder()
  .withDynamicServerList(list)
  .withRule(rule)
  .withServerListFilter(filter)
  .buildDynamicServerListLoadBalancer();
DiscoveryEnabledServer server = lb.chooseServer();


CommanBuilder.<String>newBuilder()
  .withLoadBalancer(LoadBalancerBuilder.newBuilder(0.buildFixedServerListLoadBalancer(serverList))
  .build(new LoadBalancerExecutable<String>() {
    @Override
    public String run(Server server) throws Exception {
      URL url = new URL("http://" + server.getHost() + ":" + server.getPort() + path);
      HttpURLConnection conn = (HttpURLConnection) url.openConnection();
      return conn.getResponseMessage();
    }
  }).execute();
 
```

```
```

```
```


