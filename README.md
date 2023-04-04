# resume

21.12

22.01

22.02

22.03

22.04

22.05

22.06
ocr : 안드로이드에 있던 ocr기능 서버로 분리하면서 api 만들기

22.07

22.08
메세지 분석 api V2 준비 및 출격 (phone, name, address에 대한 index, text 값 등을 모두 트래킹, 모두 개별적으로 관리 )
최초 분석 이후 이미 분석 된 값에 대해서 다시 분석하지 않도록 pre_name, pre_address, pre_phone 등을 들고 있어 response에 대한 cost, efficiency 확보
ocr : naver ocr 추가
ocr : cd - ci 설정


22.09
메세지 분석 후 결과에서 순서 로직 확정 
flask에 mysql, sqlalchemy, pymysql로 db 연결
불용어 리스트 db로 이관
약 2500 케이스에 대한 로직 test 추가
message 분석 api에 sentry 추가
dotenv 이용해서 secret 관리
ocr : GCP ocr - naver ocr 나누기
ocr : image histogram으로 이미지 비교 분석

22.10
redis cache 추가해서 자주 요청되는 주소분석 query 빠르게 처리
메모리, cpu 프로파일러 스냅샷 추가로 프로파일링 기능 추가
주소분리 api에 상세주소 분리 기능 추가
주소 검색 api를 카카오 주소검색에서 네이버 주소검색으로 변경
주소검색 전에 주소검증 추가해서 자체 주소 db에서 우선 검증과정 거치도록
주소검색 시 reverse_geocode, local 검색 추가해서 검증 -> 다시 제거
transformer로 복수 주소 간 유사도 검증 -> 다시 제거
메모리 최적화 위한 변수 삭제 및 리펙토링

22.11
메세지분석 서버 동기방식 => 비동기방식으로 전환
db sql 요청방식 수정
특수 이모지 등 처리 방식 추가
연속되는 주소 지우는 로직
이름, 불용어 추가 등을 로컬파일에서 db로 이전
지번주소, 도로명주소 유사도 거리측정으로 비교, 결정
강제지정(designation) api 새로 추가 => designation api는 분석 태우지 않음

22.12
message_tag inference api 서버 분리
db이름 리스트 스캐줄러 자동화 추가
프레임워크 flask => fastapi로 교체
ocr : naver_ocr 한번에 요청 수 3 => 8로 확대
ocr : naver_ocr response 올 때까지 계속 request 날리기
ocr : ocr 동시성 위해서 add sqs, redis, lambda 연결
ocr : flask 프레임워크에서 fastapi 프레임워크로 변경

23.01
메세지 분석 코드 리펙토링
이름 추출 함수화 + 나누기
이름 추출 api 케이스 추가 (성, 이름 갯수에 따라)
이름 추출 함수 클래스화
코드 함수화
ocr : 폴더, 탭 유저 ocr범위 추출 대응
ocr : cd-ci ec2-codedeploy 에서 ec2-elasticbeanstalk으로 변경
ocr : cv2.calcHist에서 histSize 4 -> 256으로 변경해서 더 세밀하게 판단

23.02
message analyze : 주소분석 리스트 api => 리스트로 한번에 처리하도록
ocr : 유사한 y 범위에 있는 것 x좌표로 정렬
ocr : 라인 추출(cv2.Canny, cv2.HoughLines 활용)로 범위 찾기
ocr : ocr 분석에서 grayscale로 변경해서 분석하도록


23.03
메세지 상품명 추출 api
자체 상품 카테고리 


23.04
