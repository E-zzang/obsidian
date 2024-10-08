메시지 브로커 (Redis , RabbitMQ)
데이터를 보내고, 처리하고, 삭제함.

이벤트 브로커 (Kafka, AWS Kinesis) 
- 인덱스를 통해 개별 엑세스 관리, 업무상 필요한 시간동안 이벤트 보존 가능
이벤트를 Queue 에 저장.



Replication
Master -> Slave 로 복제
장애시 수동으로 승격시켜야함 ( Sentinel 사용시 자동 )

Cluster (Replication + Scale-out)
메모리의 크기 한계와 서버 장애에 대한 대응
데이터 확장