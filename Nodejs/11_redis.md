#



### Redis:
- Redis is a in-memory data store.
- used for caching,session Storage,counter,queues

### why do we use Redis with Nodejs:
- redis is used for repeated database queries stored in memory.

```javascript

const cacheData=await redis.get('users');

if(cacheData){
    return cacheData
}

const users=User.findAll();


await redis.set(
    'users',
    JSON.stringify(users),
    {EX:300}
)

return users;

```

### what is caching:
- Caching stores frequently accessed data so the future can retrieve it faster.

benefits:
- Improve performance
- reduces database load.
- reduces repeated computation.

### Cache Invalidation:
- Process of removing or updateing the cached data when the original data changes.

Example:
- User updates their profile,delete profile.

### Cache-Aside Strategy:
- Cache-aside startegy is caching pattern when cache is not exist it again get from the db.

### diff between Redis and Mysql


Redis | Mysql |
---- | ---- |
In memory data store | relational database |
key -value data saved | table adn relationship

