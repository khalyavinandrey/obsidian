- **Redis** [обрабатывает](https://redis.io/topics/clients) каждое соединение как итерацию в цикле событий, что снижает требования к ресурсам, однако платить за это приходится тем, что каждое соединение дожидается своей очереди, при этом Redis обрабатывает запросы строго по одному.
- 
Redis способен обрабатывать наибольшее количество соединений (возможно, десятки тысяч), поскольку цикл событий помогает ему поддерживать согласованность данных, но платить за это приходится тем, что одновременно выполняется только одна операция.

#бд 