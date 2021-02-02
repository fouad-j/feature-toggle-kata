# Feature Toggle Kata

## Description
This Kata is about implementing a simple Feature Toggle mechanism based on different strategies.

Based on provided user, we have to return list of enable toggles that match these attributes (companyIdentifier, businessLine...)


## Example of entities that you can use
```java
public class FeatureToggle {
    private String featureUid;
    private boolean enable;
    private String description;
    private String strategyName;
    private List<String> strategyParams;
}
```

```java
class User {
    // auth attributes...
    private String companyIdentifier;
    private String businessLine;
    private List<String> roles;
}
```

## Rules

| RULE | featureUid       | enable | strategyName           | strategyParams |
| ---  | ---------------- | ------ | ---------------------- | ----------------------------------- |
| 1    | STATS_NEW_SCREEN | false  |                        |                                     |
| 2    | REPORT_FEATURE   | true   | BUSINESS_LINE_STRATEGY | BL_1;BL_3                           |
| 3    | MANAGE_PROFILES  | true   | ROLE_STRATEGY          | TESTER                              |
| 4    | NOTIFICATIONS    | true   | USER_STRATEGY          | user1companyId;user2companyId       |
| 5    | UPLOAD_FILES     | true   |                        |                                     |

### Rule 1
enable: false => skip it

### Rule 2
enable: true && strategyName: BUSINESS_LINE_STRATEGY => check if user businessLine match with

### Rule 3
enable: true && strategyName: ROLE_STRATEGY => check if user roles match with

### Rule 4
enable: true && strategyName: USER_STRATEGY => check if user companyIdentifier match with

### Rule 5
enable: true && strategy empty => keep it
