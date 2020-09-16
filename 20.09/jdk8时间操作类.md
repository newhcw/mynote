# jdk8 时间操作类



## 1、获取当前时间

```java
Instant instant = Instant.now(); //获取当前时间戳

LocalDate localDate = LocalDate.now();  //获取当前日期

LocalTime localTime = LocalTime.now();  //获取当前时刻

LocalDateTime localDateTime = LocalDateTime.now();  //获取当前具体时间

ZonedDateTime zonedDateTime = ZonedDateTime.now();   //获取带有时区的时间
```



## 2、 字符串转换时间

```java
String str = "2019-01-11";
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
LocalDate localDate = LocalDate.parse(str, formatter);
```



## 3、时间转为字符串

```java
LocalDate localDate = LocalDate.now();
DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
String formatDate = localDate.format(dateTimeFormatter);
System.out.println(formatDate);
```

## 4、 Date转为LocalDate

```java
Date date = new Date();
Instant instant = date.toInstant();
ZoneId zoneId = ZoneId.systemDefault();
LocalDate localDate = instant.atZone(zoneId).toLocalDate();
System.out.println(localDate);
```

## 5、LocalDate转Date

```java
LocalDate localDate = LocalDate.now();
ZoneId zoneId = ZoneId.systemDefault();
ZonedDateTime zdt = localDate.atStartOfDay(zoneId);
Date date = Date.from(zdt.toInstant());
System.out.println(date);
```

## 6、Timestamp转LocalDateTime

```java
long timestamp = System.currentTimeMillis();
Instant instant = Instant.ofEpochMilli(timestamp);
LocalDateTime localDateTime = LocalDateTime.ofInstant(instant, ZoneId.systemDefault());
System.out.println(localDateTime);
```

## 7、LocalDateTime转Timestamp

```java
LocalDateTime localDateTime = LocalDateTime.now();
long epochMilli1 = localDateTime.toInstant(ZoneOffset.ofHours(8)).toEpochMilli();// 写法 1
long epochMilli2 = localDateTime.toInstant(ZoneOffset.of("+08:00")).toEpochMilli();// 写法 2
long epochMilli3 =  localDateTime.atZone(ZoneId.systemDefault()).toInstant().toEpochMilli();// 写法 3
```