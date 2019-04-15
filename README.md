# Master-Google-Place-API
Status{statusCode=PLACES_API_ACCESS_NOT_CONFIGURED, resolution=null}


### Installing

Follow the instructions

Add the Gradle Dependancy

```
implementation 'com.google.android.libraries.places:places:1.0.0'
```

Initialize the Place API

```
 Places.initialize(getApplicationContext(), "YOUR_API_KEY");
```


Start the Autocomplete Intent

```
 List<Place.Field> fields = Arrays.asList(Place.Field.ID, Place.Field.NAME);
        Intent intent = new Autocomplete.IntentBuilder(
                AutocompleteActivityMode.OVERLAY, fields)
                .build(this);
        startActivityForResult(intent, 1101);
```


onActivityResult

```
  protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == request_code) {
            if (resultCode == RESULT_OK) {
                Place place = Autocomplete.getPlaceFromIntent(data);
                Log.i(TAG, "ManishPlace: " + place.getName() + ", " + place.getId());
                txt_search.setText(place.getName());
            } else if (resultCode == AutocompleteActivity.RESULT_ERROR) {
                // TODO: Handle the error.
                Status status = Autocomplete.getStatusFromIntent(data);
                Log.i(TAG, status.getStatusMessage());
            } else if (resultCode == RESULT_CANCELED) {
                // The user canceled the operation.
            }
        }
    }
```

![](screenrecorder.20190404230741_20190404230741.gif)
