# Vectura

**A Flutter ride-sharing app: drivers offer rides between Slovenian towns, passengers search and join them.**

![Left: sign-in screen. Right: registration screen](https://user-images.githubusercontent.com/69723817/234060872-8b8fbefa-d24d-492e-a0f7-2be5aa0d9047.png "Sign-in and registration")

![Left: home screen with the rides you offer and the rides you joined. Right: the form to offer a ride](https://user-images.githubusercontent.com/69723817/234061016-7a748b6e-4fec-4ebd-b2ed-c81132ee332f.png "Home and offer a ride")

![Ride history in the light and the dark theme, filtered by rides, my offers or all](https://user-images.githubusercontent.com/69723817/234061238-8b1a5ade-ed22-44f9-9c58-24d0dff395de.png "History, light and dark")

## Why it exists

A personal project from 2022. It is separate from the ride-sharing app I worked on during my internship at Kamino.

## How it works

| Folder | What it holds |
|---|---|
| `lib/screens/` | Sign-in, registration, home, search, offer a ride, ride details, history, profile and vehicle screens |
| `lib/bloc/` | One Bloc per screen, plus a global Bloc that streams user and ride changes to the screens that show them |
| `lib/services/` | The HTTP client and local storage |
| `lib/server/routes.dart` | The REST routes: auth (login, register, refresh), user, vehicle, rides (accept, cancel, review), ride history |

Sign-in returns a pair of JWTs. The refresh token is kept in the device keychain (`flutter_keychain`) and exchanged for a new pair through `/api/auth/refresh`. Ride details show the route on a Google Map. Search and history load page by page.

## Run it

Needs Flutter with Dart 2.15–2.x (the project predates Dart 3) and a Google Maps API key. Put the key in `android/app/src/main/AndroidManifest.xml` and `ios/Runner/AppDelegate.swift` in place of `YOUR_GOOGLE_MAPS_API_KEY`.

```sh
flutter pub get
flutter run
```

The app talks to a separate REST backend, which isn't in this repo and is no longer online. It starts, but it can't sign in.

## Tech

Flutter, Dart, flutter_bloc, Google Maps, JWT auth with the keychain, infinite scroll pagination, light and dark theme.

## Status

Finished in 2022 and archived. The backend is offline. Made by [Erik Pahor](https://github.com/MuteMuty).
