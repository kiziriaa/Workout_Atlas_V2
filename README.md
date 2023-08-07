# Workout_Atlas_V2
7-31-23 version

Instructions on how to programmatically request data from the microservice: 

r = requests.get(url = 'http://127.0.0.1:8000/workouts')

Instructions on how to programmatically receive data from the microservice:

def callback(ch, method, properties, body):
    try:
        payload_array = json.loads(body)
        for payload in payload_array:
            print(payload)
    except json.JSONDecodeError as e:
        print(' [x] Error decoding JSON:', e)
    print(' [x] Done')
    ch.basic_ack(delivery_tag=method.delivery_tag)

channel.basic_consume(on_message_callback=callback, queue=queue_name)
channel.start_consuming()

![image](https://github.com/kiziriaa/Workout_Atlas_V2/assets/102491494/d3277ded-4bb9-449f-81f0-20ea59551993)

