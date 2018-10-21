# process-order-message
#ejecutar en  local

./gradlew build shadowJar

export AMQ_URL=amqp://bzizimsp:LKVNczGhhTNTsk-CxeLgdE7MAFt_8Nbq@chimpanzee.rmq.cloudamqp.com/bzizimsp

export AMQ_QUEUE=order.procesed

java -jar build/libs/service.jar
 
 
# subir a pivotal
cf login -a https://api.run.pivotal.io

cf push --no-start

cf set-env process-order-message AMQ_URL amqp://bzizimsp:LKVNczGhhTNTsk-CxeLgdE7MAFt_8Nbq@chimpanzee.rmq.cloudamqp.com/bzizimsp

cf set-env process-order-message AMQ_QUEUE order.procesed

###Variable optenida de pivotal

cf start process-order-message

