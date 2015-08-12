일자:2/4
발제:심댈

# 메일서버

http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol

```
S: 220 smtp.example.com ESMTP Postfix
C: HELO relay.example.org
S: 250 Hello relay.example.org, I am glad to meet you
C: MAIL FROM:<bob@example.org>
S: 250 Ok
C: RCPT TO:<alice@example.com>
S: 250 Ok
C: RCPT TO:<theboss@example.com>
S: 250 Ok
C: DATA
S: 354 End data with <CR><LF>.<CR><LF>
C: From: "Bob Example" <bob@example.org>
C: To: "Alice Example" <alice@example.com>
C: Cc: theboss@example.com
C: Date: Tue, 15 January 2008 16:02:43 -0500
C: Subject: Test message
C:
C: Hello Alice.
C: This is a test message with 5 header fields and 4 lines in the message body.
C: Your friend,
C: Bob
C: .
S: 250 Ok: queued as 12345
C: QUIT
S: 221 Bye
{The server closes the connection}
```

# 메일전송 기능 요구사항

  * 메일발송내역을 알 수 있나 : 로그기록
  * 보낸 메일을 다시 보낼 수 있나 : 재전송
  * 미래 특정 시점에 보낼 수 있나 : 예약발송
  * 어플리케이션에 영향을 주지 않고 메일발송 기능을 끌 수 있나 : 메일 on/off
  * 메일서버가 죽었다. 다른 메일서버로 보내자 : 메일서버 변경기능
  * 메일이 발송되는 주기를 변경할 수 있나 (10분 -> 5분): 주기설정 기능
  * 메일발송이 실패하면? : 에러처리 (log4j, log4net)

# log4net, log4j

```
	<appender name="SmtpAppender" type="log4net.Appender.SmtpAppender">
		<to value="받는메일주소" />
		<from value="보내는메일주소" />
		<subject value="Error occurs!!!" />
		<smtpHost value="메일서버주소" />
		<authentication value="인증타입" />
        <username value="계정" />
        <password value="비번" />
		<bufferSize value="512" />
		<lossy value="true" />
		<evaluator type="log4net.Core.LevelEvaluator">
			<threshold value="ERROR" />
		</evaluator>
		<layout type="log4net.Layout.PatternLayout">
			<conversionPattern value="%newline%date [%thread] %-5level %logger [%property{NDC}] - %message%newline%newline%newline" />
		</layout>
		<threshold value="Error" />
	</appender>	
```