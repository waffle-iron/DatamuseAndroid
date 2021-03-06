[![Waffle.io - Columns and their card count](https://badge.waffle.io/CCninja86/DatamuseAndroid.png?columns=all)](https://waffle.io/CCninja86/DatamuseAndroid?utm_source=badge)
# DatamuseAndroid
A WIP Android Library for acessing the Datamuse Word API. https://www.datamuse.com/api/

### New in version 1.0.2
* Add option to either keep or reset request URL once request has been made. This allows for reuse of the same request in multiple places, i.e. build once, use anywhere.

### New in version 1.0.1
* Add ability to reuse the same DatamuseAndroid object

# How to use

## Add Gradle dependency

`implementation 'nz.co.ninjastudios.datamuseandroid:datamuse-android:1.0.2'`

## Implement Interface

`public class MainActivity extends AppCompatActivity implements DatamuseAndroidResultsListener`

```
@Override
public void onResultsSucess(ArrayList<Word> words) {
    // Your code here
}
```

## To make an API call (example for getting synonyms of a word)

### Option 1
```
boolean resetUrl = true;
new DatamuseAndroid(resetUrl).withResultsListener(myResultsListener).synonymsOf("practical").get();
```

### Option 2 (OOP + reuse same DatamuseAndroid object)

Whenever you call .get(), the request is made and then the URL is reset, allowing you to reuse the same DatamuseAndroid object for multiple queries.

```
boolean resetUrl = false;
DatamuseAndroid datamuseAndroid = new DatamuseAndroid(resetUrl);
datamuseAndroid.withResultsListener(myResultsListener);
datamuseAndroid.soundsLike("flight");
datamuseAndroid.spelledLike("f???t");
datamuseAndroid.get();
```

```
boolean resetUrl = true;
DatamuseAndroid datamuseAndroid = new DatamuseAndroid(resetUrl);
datamuseAndroid.withResultsListener(myResultsListener).soundsLike("flight").spelledLike("f???t").get();
```

### Bugs and Feature Requests

To report a bug or request a feature, open an issue. You can track progress on the waffle.io board.
