# Route53

Q. What is Amazon Route 53 Traffic Flow?

Amazon Route 53 Traffic Flow is an easy-to-use and cost-effective global traffic management service. With Amazon Route 53 Traffic Flow, you can improve the performance and availability of your application for your end users by running multiple endpoints around the world, using Amazon Route 53 Traffic Flow to connect your users to the best endpoint based on latency, geography, and endpoint health

Q. What is the difference between a traffic policy and a policy record?

A traffic policy is the set of rules that you define to route end users’ requests to one of your application’s endpoints.
By itself, a traffic policy doesn’t affect how end users are routed to your application because it isn’t yet associated with your application’s DNS name (such as www.example.com). To start using Amazon Route 53 Traffic Flow to route traffic to your application, you create a policy record which associates the traffic policy within an Amazon Route 53 hosted zone . For example, if you want to use a traffic policy that you’ve named my-first-traffic-policy to manage traffic for your application at www.example.com, you will create a policy record for www.example.com within your hosted zone example.com and choose my-first-traffic-policy as the traffic policy.

Q. Can I create an Alias record pointing to a DNS name that is managed by a traffic policy?

No, it is not possible to create an Alias record pointing to a DNS name that is being managed by a traffic policy.

Q. Does DNS Failover support Elastic Load Balancers (ELBs) as endpoints?

Yes, you can configure DNS Failover for Elastic Load Balancers (ELBs). To enable DNS Failover for an ELB endpoint, create an Alias record pointing to the ELB and set the “Evaluate Target Health” parameter to true. Route 53 creates and manages the health checks for your ELB automatically. You do not need to create your own Route 53 health check of the ELB. You also do not need to associate your resource record set for the ELB with your own health check, because Route 53 automatically associates it with the health checks that Route 53 manages on your behalf. The ELB health check will also inherit the health of your backend instances behind that ELB. For more details on using DNS Failover with ELB endpoints, please consult the Route 53 Developer Guide.

Q. What DNS record types can I associate with Route 53 health checks?

You can associate any record type supported by Route 53 except SOA and NS records.

Q. Can I health check an endpoint if I don’t know its IP address?

Yes. You can configure DNS Failover for Elastic Load Balancers and Amazon S3 website buckets via the Amazon Route 53 Console without needing to create a health check of your own. For these endpoint types, Route 53 automatically creates and manages health checks on your behalf which are used when you create an Alias record pointing to the ELB or S3 website bucket and enable the "Evaluate Target Health" parameter on the Alias record.

Q. If failover occurs and I have multiple healthy endpoints remaining, will Route 53 consider the load on my healthy endpoints when determining where to send traffic from the failed endpoint?

No, Route 53 does not make routing decisions based on the load or available traffic capacity of your endpoints. You will need to ensure that you have available capacity at your other endpoints, or the ability to scale at those endpoints, in order to handle the traffic that had been flowing to your failed endpoint.

Q. Do Route 53 health checks follow HTTP redirects?

No. Route 53 health checks consider an HTTP 3xx code to be a successful response, so they don’t follow the redirect. This may cause unexpected results for string-matching health checks. The health check searches for the specified string in the body of the redirect. Because the health check doesn’t follow the redirect, it never sends a request to the location that the redirect points to and never gets a response from that location. For string matching health checks, we recommend that you avoid pointing the health check at a location that returns an HTTP redirect.

Q. Do HTTPS health checks validate the endpoint’s SSL certificate?

No, HTTPS health checks test whether it’s possible to connect with the endpoint over SSL and whether the endpoint returns a valid HTTP response code. However, they do not validate the SSL certificate returned by the endpoint.

Q. Do HTTPS health checks support Server Name Indication (SNI)?

Yes, HTTPS health checks support SNI.

Q. Can I configure DNS Failover based on internal health metrics, such as CPU load, network, or memory?

Yes. Amazon Route 53’s metric based health checks let you perform DNS failover based on any metric that is available within Amazon CloudWatch, including AWS-provided metrics and custom metrics from your own application. When you create a metric based health check within Amazon Route 53, the health check becomes unhealthy whenever its associated Amazon CloudWatch metric enters an alarm state.