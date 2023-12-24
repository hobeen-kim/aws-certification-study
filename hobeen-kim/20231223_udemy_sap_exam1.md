# 1번

![image-20231223161225814](images/20231223_udemy_sap_exam1/image-20231223161225814.png)

- Apache Parquet 과 ORC 는 컬럼 스토리지로, 데이터를 빠르게 얻는데 최적화되어 있으며 AWS 분석 애플리케이션으로 사용됨
- 데이터를 파티셔닝함으로써 각 쿼리에 의해 스캔되는 데이터량을 줄일 수 있음
- 예를 들어 매시간 들어오는 데이터를 가진 사용자는 년, 월, 일, 시간 단위로 파티셔닝할 수 있음 (muli-level partitioning 가능)
- 따라서 문제에서 일일 단위의 분석을 하므로 일 단위로 파티셔닝을 할 수 있음

# 2번

![image-20231223162554483](images/20231223_udemy_sap_exam1/image-20231223162554483.png)

- 다른 aws 계정의 cloudwatch logs 를 모으고 합치기 위해 kinesis data firehose 를 구성할 수 있음
- 그리고 cloudwatch logs destination 을 사용하고 subscription filter 를 생성해서 중앙화된 로깅 aws account 로 로그 이벤트를 받을 수 있음
- 이 로그 이벤트 데이터는 중앙화된 kinesis firehose 스트림에서 처리와 분석으로 수행되며 읽어짐
- B 가 아닌 이유
  - cloudwatch logs agent 는 데이터를 firehose 스트림으로 넣을 수 없음

#  3번

![image-20231223163200781](images/20231223_udemy_sap_exam1/image-20231223163200781.png)

- storage gateway 는 file share 를 통해 file 을 write 할 때 자동적으로 캐시를 업데이트함.
- 하지만 s3 로 직접 올리면 캐시를 자동으로 업데이트하지 않음
- 이걸 할려면 `RefreshCache` 동작을 수행해야 함
- 이는 storage gateway 콘솔이나 aws CLI 로 가능함

# 4번

![image-20231223163417470](images/20231223_udemy_sap_exam1/image-20231223163417470.png)

- secret manager 는 VPC private subnet 에 있는 aws 서비스는 인터넷 접근이 안되기 때문에 secret 을 rotate 할 수 없음
- 따라서 rotate 하려면 vpc interface endpoint 를 구성해서 secret manager lambda function 과 RDS 인스턴스에 접근 가능하도록 해야 함

# 6번

![image-20231223164001940](images/20231223_udemy_sap_exam1/image-20231223164001940.png)

- kms:GenerateDataKey : aws kms 의 외부에서의 사용을 위해 고유한 symmetric data key 를 반환함
  - 이 동작은 data key 의 plaintext 복사본과 사용자가 지정한 symmetric encryption KMS 키로 암호화된 복사본을 반환함
  - plaintext key 안의 바이트들은 랜덤이며 caller 나 KMS 키와 관련없음
  - plaintext key 로 AWS KMS 외부의 데이터를 암호화하는 데 사용할 수 있고 encrypted data 로 encrypted data key 를 저장할 수 있음
- 오답
  - kms:GetPublicKey - This option returns the public key of an asymmetric KMS key. Unlike the private key of an asymmetric KMS key, which never leaves AWS KMS unencrypted, callers with kms:GetPublicKey permission can download the public key of an asymmetric KMS key. It cannot be used for a client-side encryption mechanism.
  - kms:GetKeyPolicy - This option gets a key policy attached to the specified KMS key. It cannot be used for a client-side encryption mechanism.
  - kms:GetDataKey - This is a made-up option that serves as a distractor.

# 8번

![image-20231223164823410](images/20231223_udemy_sap_exam1/image-20231223164823410.png)

- x-ray 는 microservice architecture 에서 특정 서비스나 이슈를 분석하는 데 사용할 수 있는 데이터를 추적하는데 사용
- cloudwatch 는 인프라의 매트릭을 수집할 수 있게 함

# 9번

![image-20231223171041841](images/20231223_udemy_sap_exam1/image-20231223171041841.png)

`