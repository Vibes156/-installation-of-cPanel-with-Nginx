# installation-of-cPanel-with-Nginx

How to Install and Manage NGINX on cPanel
Although Apache and NGINX are both web servers, they approach the task of serving web pages differently. Each has advantages and trade-offs, which prompts the question: can I use NGINX with cPanel? 

The short answer is yes, you can use NGINX with cPanel; however, its integration is a little tricky. Let’s explore the ways cPanel users can take advantage of NGINX’s strengths, and look at how we are working to make NGINX a viable alternative to Apache on cPanel servers.

cPanel and Apache have decades of shared history, and Apache is deeply integrated into cPanel, which depends on Apache for many of its features. NGINX currently serves 32 percent of websites, versus Apache accounting for 37 percent of websites served on the internet. So what is NGINX, and what does it do differently than Apache?

What Is NGINX, and How Does NGINX Work?
NGINX is a web server, load balancer, and reverse caching proxy. Like all web servers, it accepts HTTP requests and responds with HTML documents. NGINX was developed in response to perceived weaknesses in the way Apache handled network connections and requests.

Initially, Apache operated on a process-per-connection model, spawning a process for every web request. Each process was tied to a specific request and consumed a significant chunk of the host server’s resources, particularly memory. That model worked well on the early web, but modern web servers are expected to handle hundreds of concurrent connections, rapidly consuming the server’s resources.

NGINX, in contrast, has an asynchronous event-driven architecture. A master process controls worker processes, which respond to events, typically new connections, and each worker can handle multiple connections. Because workers are non-blocking, they respond to events as they occur, processing requests in turn rather than being dedicated to a single connection.

In recent years, especially with the release of Apache 2.4, Apache’s developers have worked to improve performance with new multi-processing models (MPMs), such as worker MPM and event MPM. MPMs help improves overall resource consumption, but Apache can still become resource-constrained when asked to handle too many requests.

Is NGINX Better Than Apache?
There is no simple answer to which web server is better; the only appropriate response is to ask: better for what? The differences in how Apache and NGINX are designed have implications that impact their features and performance.

NGINX is undoubtedly faster at serving static content, and benchmarks show that NGINX serves static files almost twice as fast while consuming less memory. However, NGINX cannot serve dynamic content and relies on external programs to handle the processing, whereas Apache uses internal modules. Benchmarks show that Apache and NGINX response times and concurrency handling for dynamic content are approximately equal, depending on the specifics of the scenario.

Because Apache is extensible with modules, it is easy for web hosts to add new modules to control Apache’s behavior. NGINX is configurable, but it lacks the extensibility of Apache. Adding new features to NGINX often requires recompiling, making it difficult to activate and deactivate functionality on the fly.

Local Web Server Configuration
Apache tends to be slower at serving static content than NGINX because it needs to check configuration files for each connection in the .htaccess file. With local .htaccess files, shared hosting clients and web applications can make changes to Apache’s configuration.

NGINX lacks an equivalent local configuration mechanism, working with a central configuration file. There is no way for shared hosting clients to configure NGINX because all changes have to be made by the server’s system administrator. 

The absence of an .htaccess file can impact shared hosting for applications, such as WordPress, which depend on the ability to edit local configuration files for features such as custom permalinks. This is why shared hosting providers rarely use NGINX as an alternative to Apache.

Apache and NGINX excel in different situations, with Apache offering adequate performance in most web hosting scenarios with superior customization and flexibility. NGINX provides better performance in scenarios with large numbers of concurrent connections. It is, however, possible to take advantage of the strengths of Apache and NGINX combined.

cPanel with NGINX as a Reverse Proxy
In addition to being a web server, NGINX is also a powerful reverse proxy and cache. A reverse proxy sits between the client (a web browser) and the server—in this case, Apache, accepting connections from the client and passing them on to the server.

When used as a reverse proxy, NGINX is very fast at serving static content while passing dynamic content onto Apache. Additionally, NGINX can act as a cache for Apache. When used as a caching mechanism, NGINX caches dynamic content for Apache and responds directly to future requests for the same content. Using NGINX with cPanel as a reverse caching proxy can substantially increase performance and reduce server load.

It is possible to manually install NGINX with Apache on a cPanel server, but installing Engintron is a faster and easier process. Engintron is a cPanel app that integrates NGINX with your cPanel server. When installing Engintron, it configures NGINX as a reverse caching proxy for static files with a caching layer for dynamic content from software such as WordPress or Magento. Utilizing cPanel’s ea-nginx script will also create a reverse proxy; however, it does not set up a caching layer for dynamic content. 

Replacing Apache with NGINX on cPanel
Currently, NGINX cannot be used as a drop-in replacement for Apache, because many cPanel features depend on Apache. However, we are working towards making NGINX an alternative cPanel web server.

Last year, we released an experimental version of EasyApache integrating NGINX, which did not wholly replace Apache but focused on using NGINX in some key areas, focusing primarily on WordPress support. We’re continuing to improve NGINX integration and recently added redirect and subdomain support to the experimental release.

NGINX support is still experimental, and we advise against using NGINX as an Apache replacement in production cPanel servers.

While there are alternatives to using NGINX as a drop-in replacement for Apache on cPanel servers, the path forward for a standalone NGINX web server is a work in progress. Hopefully, these scenarios help better inform your decisions on which web server is best for you.

If you have any further questions about installing and managing NGINX on cPanel or just want to talk about all things cPanel & WHM, please join us on our official Discord channel, our official cPanel subreddit, or our Support Forum.
