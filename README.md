# CT484-01

Lab of the Mobile Application Development course.

## Student

ID: B1910013  
Name: Nguyen Thanh Trung

## Setup

Clone this project to local.

### Firebase

Authentication: Email/Password  
Realtime Database: Rules in LOCKED MODE and add this rule  
{
  "rules": {
    ".read": "auth.uid != null",
    "products": {
      ".indexOn": "creatorId",
      "$productId": {
        ".validate": "newData.hasChildren(['creatorId', 'title', 'description', 'imageUrl', 'price'])",
        ".write": "!data.exists() || data.child('creatorId').val() == auth.uid"
      }
    },
    "userFavorites": {
      "$uid": {
        ".write": "$uid == auth.uid"
      }
    }
  }
}

### Enviroment Config

Create .env file in project root folder & add your firebase project information:  

FIREBASE_API_KEY=Web API Key from Firebase Project  
FIREBASE_URL=URL to Realtime Database on Firebase  

Example:  
FIREBASE_API_KEY=AIzaSyDFRZjhIF-OLnDpVeleWpRcoUZPBs5eyHA  
FIREBASE_URL=https://flutter-myshop-project-ct484-default-rtdb.asia-southeast1.firebasedatabase.app/  

### Install all the missing packages in flutter project

Command: flutter pub get  