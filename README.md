# Json in C&#35;

데이터 직렬화 및 역직렬화
- 직렬화(Serialize): C# 개체를 JSON 문자열로 변환하는 작업
- 역직렬화(Deserialize): JSON 문자열을 C#개체로 변환

  
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/27d0b706-0317-4303-a72f-9cd3b7862962)


- txt파일에 json데이터 Write
 public static void Main()
        {
            string path = @"C:\Users\CNSI-JJW\OneDrive\바탕 화면\Office2021\ggg.txt";
            string[] userList = new string[4] { "USER1", "USER2", "USER3", "USER4" };
            string users = string.Empty;
            JObject configData = new JObject(
                new JProperty("IP", "127.0.0.1"),
                new JProperty("PORT", "8888"),
                new JProperty("DATABASE", "DB TEST"),
                new JProperty("ID", "TEST ID"),
                new JProperty("PASSWORD", "1234")
            );
            configData.Add("USERS", JArray.FromObject(userList));
            File.WriteAllText(path, configData.ToString());
        }
  
  ------------------------------------------------------------------------------------------------

  * 1. 파일 경로 지정
       => string 파일경로 변수명 = @"파일 경로\파일명.확장자";
       
  * 2. JObject 생성
       => JObject란?
          - JSON Object를 의미한다.
          - JObject 자체가 name을 가질 수 없다.
          - '키:값' pair를 가진다.
          - 
  * 3. JProperty("키", "값") 대입
       => new JProperty("키1", "값1"),
          new JPropeerty("키2", "값2")
       
  * 4. JObject에 String 배열 넣기
       => JObject객체명.Add("추가되는 배열의 KEY 이름", JArray.FromObject(배열명));

  * 5. 파일에 JSON 데이터 Write하기
       => File.WriteAllText(write할 경로, JObject변수명.ToString());

       
