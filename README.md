<!--hide-->
# SMS Queue Management System
<!--endhide-->

Let's create a Queue System: Queue systems are heavily used in Government institutions, airports, banks, and many other venues looking to organize the incoming traffic.

Queue systems can also be used to load balancing for different applications like:

- Establishing priorities in web servers' incoming requests.
- Immigration and visa applications that need to be prioritized.
- Network packages.
- etc.

<onlyfor saas="false" withBanner="false">

## 🌱  How to start this project

Do not clone this repository! You will be using a different template.

We recommend opening the `python boilerplate`, using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can [clone the GitHub repository](https://4geeks.com/how-to/github-clone-repository) on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```sh
$ git clone https://github.com/4GeeksAcademy/flask-rest-hello
```

💡 Important: Remember to create a new repository, update the remote (`git remote set-url origin <your new url>`), and upload the code to your new repository using `add`, `commit` and `push`.

</onlyfor>

## 📝 Instructions

- The API has to integrate with Twillio API to be able to send SMS to notify users when their turn has arrived.

- Create an API that allows clients to manage a simple Queue, and use the following data structure to implement the queue:

```py
class Queue:

    def __init__(self):
        self._queue = []
        # depending on the _mode, the queue has to behave like a FIFO or LIFO
        self._mode = 'FIFO'

    def enqueue(self, item):
    def dequeue(self):
    def get_queue(self):
    def size(self):
        return len(self._queue) 
```

## Example workflow

1. The API receives a request to add Bob into the queue (`POST /new`) with any particular priority (FIFO or LIFO).
2. The API ads Bob and notifies him with an SMS confirmation, the SMS must say how many people are in front of him on the line.
3. The system now waits until the enpoint `GET /next` gets executed to process the person on the queue.
4. Every time a `GET /next` request is received, the next person on the queue gets processed until it is Bob's turn.
5. When Bob is processed, the system sends him another SMS to let him know that his turn has arrived and deletes him from the list.

## More details

1. You have to create 3 endpoints for your API:

- POST `/new`: Will receive information about a user and add him to the queue.  
- GET `/next`: Will process one spot of the queue.  
- GET `/all`: Will return a list with everyone that is pending to be processed (the current queue). 

## 📖 Fundamentals

This exercise will make you practice the following fundamentals:

1. Here you can find the information on [how to send a sms with twillio](https://www.twilio.com/docs/sms/send-messages), you will have to register an account (free) and also register a number (free)
4. Building a RESTful API
5. Complex Data Structures.
6. Queue (FIFO vs FILO)
7. SMS.
