# java-secrets-in-mem
This is an example of dumping java memory to find a password which was stored as `String`

# running
```bash
./gradlew :build

java -jar build/libs/java-secrets-in-mem-0.0.1-SNAPSHOT.jar
```

# adding passwords to the jar file
```bash
curl -vv http://localhost:8080/cars -H 'Authorization: Basic dXNlcjpwYXNzd29yZA=='
curl -vv http://localhost:8080/cars -H 'Authorization: Basic dXNlcjpoZWFwLXNwcmF5'
```

# dump the mem
```bash
jmap -dump:format=b,file=dump.dump $PID

strings dump.dump | grep $PASSWORD
```
