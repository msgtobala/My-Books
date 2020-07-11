

# Firestore And Flutter

1. Create a Firebase project using mail id

2. Choose database as `Firestore`

3. Select rules for test mode -> dev, production mode -> production

4. Create a flutter project using `flutter create <app-name>`

5. Change / copy the package name to setup connection between app and the firestorm

6. For **Android**, go to android > app > src > main > AndroidManifest.xml

   1. Change the desired package name
   2. kje

7. For **iOS**, open the ios folder in Xcode. Open runner workspace file.Go to runner

   1. Change the desired package name(should be same as android domain)

8. Go to guide with the link [Firebase for firestore](https://firebase.google.com/docs/flutter/setup?authuser=0) for the setup (choose iOS and android)

   Guidelines are as follows,

   For **Android**,

   * Once in the created project, go to **Project overview** by selecting the option from the side bar

   * Choose android option

   * Add package name as created in the step 6

   * Click Register app

   * Download `google-services.json`

   * Paste the file into android > app folder

   * Go the andoird > build.gradle, check the following

     ```java
     buildscript {
     
         repositories {
           // Check that you have the following line (if not, add it):
           google()  // Google's Maven repository
         }
     
         // ...
     
         dependencies {
           // ...
     
           // Add the following line:
           classpath 'com.google.gms:google-services:4.3.3'  // Google Services plugin
         }
     }
     
     allprojects {
         // ...
     
         repositories {
           // Check that you have following line (if not, add it):
           google()  // Google's Maven repository
           // ...
         }
     }
     ```

   * Go to android > app > build.gradle

     ```java
     // Add the following line:
     apply plugin: 'com.google.gms.google-services'  // Google Services plugin
     ```

   android {
     // ...
   }

   // paste this along with apply plugin
     ```
   
   * Click next and go to console again(for ios setup)
   
   For **iOS**,
   
   * click on ios option
   * Copy paste the package name
   * Click register app
   * Download plist file
   * Paste into Runner > Runner(using Xcode).
     ```

9. Add **Firestore plugins**

   1. [Core Plugin](https://pub.dev/packages/firebase_core#-readme-tab-)
   2. [Cloud Firestore](https://pub.dev/packages/cloud_firestore)

**HURAAYY!!! DONE WITH SETUP**

### Queries

**Creating database instance**

```dart
Firestore _db = Firestore.instance;
```

**setData** into a collection

> A document will be added in `Products` collections with the document id `productId`. This will also act as update method.
>
> If there is no document with the id, it will be newly added.If there is already a document with the querying id, it will be updated

```da
_db.collection('products').document(product.productId).setData(product.toMap());
```

**Get Data** from a collection

```dart
Stream<List<ProductModel>> getProducts() {
  return _db.collection('products').snapshots().map(
    (snapshot) => snapshot.documents
    .map((document) => ProductModel.fromFireStore(document.data))
    .toList(),
  );
}

ProductModel.fromFireStore(Map<String, dynamic> firestore)
      : productId = firestore['productId'],
        productName = firestore['productName'],
        productPrice = firestore['productPrice'];
```

**Delete document**

```dart
_db.collection('products').document(<documentId>).delete();
```

































