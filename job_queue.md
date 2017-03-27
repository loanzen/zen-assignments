# Job Queue for Python

Implement a python library that allows queuing jobs and processing them in background with workers. It should be backed by some persistent storage like 
(redis/rabbitmq/kafka) and should be simple to use. It should be possible to access the results of the job from the calling code. 

To make thing interesting, we would like the workers to use the [asyncio](https://docs.python.org/3/library/asyncio.html) concurrency module by default. 

Some of the other (optional) features that would be great to have are

1) `retry`: A configurable settings that allows task to be retried in case it fails. Should use exponential backoff for the same

2) `priority`: Ability to have some kind of priority in between tasks

3) `configurable`: Should be able to support multiple difference concurency paradigm like `multicprocessing/threading/gevent` for workers

4) Finally it should be possible to run it in async mode without using any persistent backend but implementing producer/consumer using `asyncio` based queue

5) Some other feature that you could think off.


### Example


	def add(x, y):
    	return x + y
    	
    
	job = add.delay(3, 4)
	time.sleep(1)
	print job.result
