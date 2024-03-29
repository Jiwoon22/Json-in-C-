
**[ json 데이터 다룰 때, 알아야 하는 필수 개념 ]**

- JObject

JObject 클래스는 JSON 객체를 나타냅니다. JSON 객체는 중괄호 {}로 둘러싸인 키-값 쌍의 집합을 의미합니다.

JObject는 특정 JSON 데이터가 객체인 경우 사용됩니다. 즉, 데이터가 중괄호로 둘러싸인 경우입니다.

객체 내의 키-값 쌍을 효율적으로 다룰 수 있습니다. 예를 들어, jsonObject["key"]와 같은 형태로 특정 키의 값을 가져올 수 있습니다.
<br/> <br/> 

- JToken

JToken은 JSON 데이터 구조에서의 단일 요소를 나타냅니다.


JSON의 모든 종류의 데이터 유형을 나타낼 수 있습니다. 객체, 배열, 속성, 값 등을 포함합니다.


JObject, JArray, JProperty, JValue 등의 파생 클래스를 가집니다.


JToken은 LINQ를 사용하여 쿼리할 수 있으며, Children(), Descendants(), SelectToken(), SelectTokens() 등의 메서드를 제공합니다.


예를 들어, JObject나 JArray에서 특정 속성이나 요소를 찾거나 조작하는 데 사용됩니다.
<br/> <br/> 

- JProperty

JProperty는 JSON 객체 안에서의 키와 값의 쌍을 나타냅니다.

JSON 객체의 속성을 표현하며, JToken의 파생 클래스입니다.

JProperty는 키와 값을 직접 접근할 수 있으며, 이는 Name 및 Value 속성을 통해 이루어집니다.

예를 들어, JSON 객체에서 특정 키의 값을 찾거나 변경하는 데 사용됩니다.


  
<br/> <br/> 
  **[ 데이터 직렬화 및 역직렬화 ]**
- 직렬화(Serialize): C# 개체를 JSON 문자열로 변환하는 작업
- 역직렬화(Deserialize): JSON 문자열을 C#개체로 변환
<br/> <br/> 
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/d0e4d69f-6ba5-4374-97c7-884d561299dd)

  
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/27d0b706-0317-4303-a72f-9cd3b7862962)



<br/> <br/> <br/> <br/> 
**[ txt파일에 json데이터 Write ]**

  ![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/4a5f35c6-e095-4e10-b604-cddb574a94b6)


  ------------------------------------------------------------------------------------------------
  

  * 1. 파일 경로 지정
       => string 파일경로 변수명 = @"파일 경로\파일명.확장자";
       
  * 2. JObject 생성
       => JObject란?
          - JSON Object를 의미한다.
          - JObject 자체가 name을 가질 수 없다.
          - '키:값' pair를 가진다.
            
  * 3. JProperty("키", "값") 대입
       => new JProperty("키1", "값1"),
          new JPropeerty("키2", "값2")
       
  * 4. JObject에 String 배열 넣기
       => JObject객체명.Add("추가되는 배열의 KEY 이름", JArray.FromObject(배열명));

  * 5. 파일에 JSON 데이터 Write하기
       => File.WriteAllText(write할 경로, JObject변수명.ToString());

------------------------------------------------------------------------------------------------ <br/>  <br/> 
**Json데이터를 클래스 객체로 다루기 (역직렬화 -> 직렬화)**
 <br/>  <br/> 
	1. Json데이터의 구조를 파악
	2. 구조에 맞는 클래스 선언
	3. 선언된 클래스 자료형으로 json데이터의 역직렬화( json->c#개체 변환 )
  4. 클래스의 멤버변수로 접근해서 value 수정 가능
 <br/>  <br/> 
<예제 코드>
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/9a129104-1c8a-43a2-90d4-f88d6771766f)
 <br/>  <br/> 
위 json 데이터의 구조는 Key가 2개 존재하고
"SalesRecord" Key는 json(Key:Value)데이터가 List형태로 존재한다.
그렇기 때문에 json데이터가 하나 더 존재하므로 date,item,price,quantity,total을 포함하는 클래스를 하나 더 선언해야 한다. <br/>  <br/> 
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/c2a8e897-b277-4df9-9220-5a797c4b0e11) <br/>  <br/> 

1,2 과정을 전부 거쳤으면 3의 과정을 수행한다.
![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/5e8d2b53-323e-4038-bdf2-5f1ff8ef9760)<br/>  <br/> 
선언해둔 Item 클래스 자료형으로 json데이터를 역직렬화 한 뒤
수정하고 싶은 json 데이터에 접근하여 value를 수정한다.

수정 과정을 거친 후에, 다시 직렬화를 수행한 뒤, 직렬화된 string 변수를 파일에 Write하여 원본 json에 수정 내용이 반영되도록 한다.![image](https://github.com/Jiwoon22/Json-in-C-/assets/51106092/28b77dfb-9db2-47ca-82be-adc53bb03246)



       
