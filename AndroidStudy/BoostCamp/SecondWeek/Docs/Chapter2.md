# 인텐트와 액티비티 실행 살펴보기

## 인텐트의 이해
- 인텐트는 액티비티를 실행시키거나, 브로드캐스트에 데이터를 전달하거나 서비스와 통신을할 수 있게 해준다.
- 인텐트는 어떠한 행위를 추상적으로 설명해준다.
- 메시지 객체.
- 앱끼리 데이터를 주고 받거나 액티비티를 실행하는 용도로 가장 많이 사용된다.

### 인텐트 구조
#### Action
- 행위에 대한 정보이다.
- 대표적으로 ACTION_VIEW, ACTION_EDIT, ACTION_MAIN 등이 있다.
#### Data
- 행위에서 필요한 정보들을 가지고있다.
- Uri로 표현한다. 예를들면 주소록에 저장되어있는 사람을 가리킨다.
```
ACTION_VIEW content://contacts/people/1
 -> Display information about the person whose identifier is "1".
ACTION_DIAL tel:123
 -> Display the phone dialer with the given number filled in.
```
#### Category
- 행위에 대한 부가적인 정보.
- 예를들면 CATEGORY_LAUNCHER.
#### Type
#### Component
#### Extras
- Bundle 형태로 저장되어있는 부가적인 정보들.
- 컴포넌트에게 제공할 추가적인 데이터로 사용한다.

### 인텐트의 종류
#### 명시적 인텐트
- 목표 컴포넌트를 설정한 인텐트이다. 
- Class를 지정하여 액티비티 또는 서비스를 실행시킬 수 있다.
#### 암시적 인텐트
- 목표 행위에 대한 정보만을 가지고 있는 인텐트이다.
- 시스템이 행위가 가능한 컴퓨넌트를 탐색하여 결정한다.
- 묵시적 인텐트에 대해 앱이 반응하기 위해서는 매니페스트에 IntentFilter가 등록되어있어야한다.
- 동영상 플레이어 또는 문서 작성 프로그램 찾기.

### Standard Activity Actions
ACTION_MAIN
ACTION_VIEW
ACTION_ATTACH_DATA
ACTION_EDIT
ACTION_PICK
ACTION_CHOOSER
ACTION_GET_CONTENT
ACTION_DIAL
ACTION_CALL
ACTION_SEND
ACTION_SENDTO
ACTION_ANSWER
ACTION_INSERT
ACTION_DELETE
ACTION_RUN
ACTION_SYNC
ACTION_PICK_ACTIVITY
ACTION_SEARCH
ACTION_WEB_SEARCH
ACTION_FACTORY_TEST
### Standard Broadcast Actions
ACTION_TIME_TICK
ACTION_TIME_CHANGED
ACTION_TIMEZONE_CHANGED
ACTION_BOOT_COMPLETED
ACTION_PACKAGE_ADDED
ACTION_PACKAGE_CHANGED
ACTION_PACKAGE_REMOVED
ACTION_PACKAGE_RESTARTED
ACTION_PACKAGE_DATA_CLEARED
ACTION_PACKAGES_SUSPENDED
ACTION_PACKAGES_UNSUSPENDED
ACTION_UID_REMOVED
ACTION_BATTERY_CHANGED
ACTION_POWER_CONNECTED
ACTION_POWER_DISCONNECTED
ACTION_SHUTDOWN
### Standard Categories
CATEGORY_DEFAULT
CATEGORY_BROWSABLE
CATEGORY_TAB
CATEGORY_ALTERNATIVE
CATEGORY_SELECTED_ALTERNATIVE
CATEGORY_LAUNCHER
CATEGORY_INFO
CATEGORY_HOME
CATEGORY_PREFERENCE
CATEGORY_TEST
CATEGORY_CAR_DOCK
CATEGORY_DESK_DOCK
CATEGORY_LE_DESK_DOCK
CATEGORY_HE_DESK_DOCK
CATEGORY_CAR_MODE
CATEGORY_APP_MARKET
CATEGORY_VR_HOME
### Standard Extra Data
EXTRA_ALARM_COUNT
EXTRA_BCC
EXTRA_CC
EXTRA_CHANGED_COMPONENT_NAME
EXTRA_DATA_REMOVED
EXTRA_DOCK_STATE
EXTRA_DOCK_STATE_HE_DESK
EXTRA_DOCK_STATE_LE_DESK
EXTRA_DOCK_STATE_CAR
EXTRA_DOCK_STATE_DESK
EXTRA_DOCK_STATE_UNDOCKED
EXTRA_DONT_KILL_APP
EXTRA_EMAIL
EXTRA_INITIAL_INTENTS
EXTRA_INTENT
EXTRA_KEY_EVENT
EXTRA_ORIGINATING_URI
EXTRA_PHONE_NUMBER
EXTRA_REFERRER
EXTRA_REMOTE_INTENT_TOKEN
EXTRA_REPLACING
EXTRA_SHORTCUT_ICON
EXTRA_SHORTCUT_ICON_RESOURCE
EXTRA_SHORTCUT_INTENT
EXTRA_STREAM
EXTRA_SHORTCUT_NAME
EXTRA_SUBJECT
EXTRA_TEMPLATE
EXTRA_TEXT
EXTRA_TITLE
EXTRA_UID

## 액티비티 실행방법
- 명시적
```java
Intent intentC = new Intent(this , ActivityC.class);
```
- 암시적
```java
Intent callntent = new Intent(Intent.ACTION_CALL);
callntent.setData(Uri.parse("tel:"+phone));
```