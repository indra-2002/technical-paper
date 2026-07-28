
## Introduction

Our project is experiencing performance and scalability issues because the application repeatedly retrieves the same data from the database. As the number of users increases, the database receives many identical requests, which increases response time and server load. To improve performance, our team decided to investigate different caching approaches. Caching stores frequently accessed data in temporary high-speed storage so that future requests can be served quickly without repeatedly accessing the database.

## What is Caching?

Caching is a technique for storing frequently accessed data in temporary storage, called a cache. When the same data is requested again, the application first checks the cache. If the data is available, it is returned immediately without querying the database. This reduces response time and improves application performance.

## Understanding Caching with an Instagram Example

Instagram is a good example of how caching works in real-world applications.

When a user opens an Instagram profile, the application displays information such as:

* Profile picture
* Username
* Bio
* Highlights
* Posts
* Followers count
* Following count

Some of this information changes very rarely. For example, the profile picture, username, bio, highlights, and older posts usually remain the same for a long time. Instagram can cache this information so that future requests are served quickly without accessing the database.

However, some information changes continuously, such as:

* Likes
* Comments
* Story views
* Direct messages
* Notifications
* Online status

For example, if a post receives thousands of likes every minute, displaying an outdated cached value would be incorrect. Therefore, this type of data is refreshed frequently or retrieved directly from the database.

## Different Caching Approaches

### In-Memory Cache

In-memory caching stores data inside the application’s RAM. Since the data is available in memory, retrieval is extremely fast. This approach is suitable for applications running on a single server.

### Distributed Cache

A distributed cache stores data on dedicated cache servers that are shared by multiple application servers. This approach is commonly used in scalable cloud applications.

### Database Cache

Many database systems cache frequently executed queries and data pages. This reduces the number of expensive database operations and improves query performance.

### Content Delivery Network (CDN)

A CDN caches static resources such as images, videos, JavaScript files, and CSS files on servers located around the world. Users receive content from the nearest server, reducing latency and improving page loading speed.

## Best Practices

* Cache frequently accessed data.
* Avoid caching data that changes every second.
* Configure an appropriate cache expiration time.
* Update or remove cached data when the original data changes.

## Conclusion

Caching is an effective technique for improving application performance and scalability. It reduces database load, decreases response time, and improves the user experience. Choosing the appropriate caching strategy depends on how frequently the data changes and how often it is accessed. Large applications such as Instagram use multiple caching techniques to efficiently serve millions of users.

## References

* https://youtu.be/xBTGln828Ps?si=jPyNQyKmZazr0nBc
* https://aws.amazon.com/caching/
