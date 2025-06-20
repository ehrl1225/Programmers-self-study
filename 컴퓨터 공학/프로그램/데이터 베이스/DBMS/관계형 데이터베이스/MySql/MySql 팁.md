

# insert 할 때 자동 생성된 ID 값 가져오기

```java
public int insertWiseSaying( String content, String author){  
    PreparedStatement stmt;  
    int id = 0;  
    try{  
  
        stmt = conn.prepareStatement(getInsertSql(content, author), Statement.RETURN_GENERATED_KEYS);  
        stmt.executeUpdate();  
        ResultSet rs = stmt.getGeneratedKeys();  
        if(rs.next()){  
            id = rs.getInt(1);  
        }  
        stmt.close();  
    }catch (SQLException e){  
        System.out.println("sql failed" + e.getMessage());  
    }  
    return id;  
}
```
이런 식으로 하면 됨

# 데이터베이스 주소와 아이디와 비번 가져오기

```java
Properties properties = new Properties();
try {
  properties.load(new FileInputStream("db.properties"));
} catch (IOException e){
  e.printStackTrace();
}
URL = properties.getProperty("URL");
USERNAME = properties.getProperty("USERNAME");
PASSWORD = properties.getProperty("PASSWORD");
```
이렇게 하면 될거임
물론 암호화 해두면 좋을 듯


# 데이터베이스 매개변수 값 넣기
```java
String query = "insert into wisesaying (content, author) values (?, ?)";
PreparedStatement preparedStatement = connection.prepareStatement(query, Statement.RETURN_GENERATED_KEYS);
preparedStatement.setString(1, content);
preparedStatement.setString(2, author);
```
이런식으로 가능함