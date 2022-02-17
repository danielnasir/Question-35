import requests
import json

class Post:
    def __init__(self,d):
        self.__dict__=d

    def __str__(self):
        r=""
        for k,v in self.__dict__.items():
            r += f'{k} : {(str)(v)} \n'
        return r

id= (input('Plese select post id'))
response=requests.get('https://jsonplaceholder.typicode.com/posts/'+id)

if response.status_code//100==2:
    postjs=json.loads(response.content)
    post=Post(postjs)
    print (post)

else:
    print('this id does not exist')
