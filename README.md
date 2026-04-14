# Siperb - Browser Phone
A fully featured browser based WebRTC Softphone phone for Asterisk or FreeSWITCH PBX

### About Siperb
Siperb provides both the [Softphone](https://www.siperb.com/kb/article/softphone/) and the [SIP to WebRTC Proxy](https://www.siperb.com/kb/article/webrtc-to-sip-proxy/) that sits in the cloud between your existing PBX and your users.
Utilize your existing PBX to seamlessly integrate with the advanced [WebRTC](https://www.siperb.com/kb/article/what-is-webrtc/) capabilities we provide. At Siperb, we act as a proxy, bridging your current systems to our robust WebRTC client. This setup allows you the flexibility to connect with us directly or continue independently if your PBX is fully WebRTC capable. Choose the path that best suits your infrastructure needs. [Learn more about Siperb](https://www.siperb.com/)

## Browser Phone v0.3.x
> [!NOTE]
> Browser Phone is a free and open-source project. You can download this repo and use it as-is or incorporate it into your own project free of charge. Browser Phone has been downloaded thousands of times, and this repo is currently cloned many times per day. To get support for Browser Phone go to the [Siperb Discussion Forum](https://github.com/orgs/Siperb/discussions). If you require technical support, or provisioning services, syncing, storage, then rather opt for the [Siperb Hosted Solution](https://www.siperb.com/phone/)

## Features v0.3.x
- SIP Audio Calling
- SIP Video Calling
- XMPP Messaging
- Call Transfer (Both Blind & Attended)
- 3rd Party Conference Call
- Call Detail Records
- Call Recording (Audio & Video)
- Screen Share during Video Call
- Scratchpad Share during Video Call
- Video/Audio File Share during Video Call
- SIP (text/plain) Messaging
- SIP Message Accept Notification (not delivery)
- Buddy (Contact) Management
- Useful debug messages sent to console.
- Works on: Chrome (all features work), Edge (same as Chrome), Opera (same as Chrome), Firefox (Most features work), Safari (Most feature work)
- Asterisk SFU - Including talker notification and Caller ID
- Dark Mode & Light Mode - System Setting Detects

## Server; Requires
- Asterisk PBX version 13|16+ (with Websockets and Text Messaging, chan_sip or chan_pjsip)

## JavaScript Dependencies
- sip-0.20.0                    : WebRTC and SIP signalling library
- jquery-3.3.1                  : JavaScript toolkit
- jquery.md5                    : Md5 Hash plug-in (unused)
- Chart-2.7.2                   : Graph and Chart UI
- jquery-ui                     : Windowing & UI Library
- fabric-2.4.6                  : Canvas Editing Library
- moment-2.24.0                 : Date & Time Library
- croppie-2.6.4                 : Profile Picture Crop Library
- strophe-1.4.1                 : XMPP Library

> Note: These files will load automatically from CDN.

## StyleSheet Dependencies
- normalize-v8.0.1              : CSS Normalising Stylesheet
- roboto                        : Roboto Font
- font-awesome-4.7              : Icon Font library
- jquery-ui                     : For jQuery UI
- croppie-2.6.4                 : For Croppie

> Note: These files will load automatically from CDN.

## Remote Configuration (`setconfig.html`)

`setconfig.html` allows the phone to be pre-configured via URL query parameters — useful for provisioning links, QR codes, or single-sign-on redirects. When opened, it writes the supplied values into `localStorage` and immediately redirects to `index.html`.

**Usage:**
```
setconfig.html?server=sip.example.com&port=8089&path=/ws&domain=example.com&display_name=Alice&sip_username=alice&sip_password=secret
```

**Supported parameters:**

| Parameter      | localStorage key     | Description                        |
|----------------|----------------------|------------------------------------|
| `server`       | `wssServer`          | WebSocket server hostname          |
| `port`         | `WebSocketPort`      | WebSocket server port              |
| `path`         | `ServerPath`         | WebSocket server path              |
| `display_name` | `profileName`        | User's display name                |
| `domain`       | `SipDomain`          | SIP domain                         |
| `sip_username` | `SipUsername`        | SIP username                       |
| `sip_password` | `SipPassword`        | SIP password                       |

All seven parameters are required. If any are missing, an error page is shown instead of redirecting. The following settings are also written with defaults if not already present in `localStorage`:

| localStorage key     | Default  |
|----------------------|----------|
| `VoicemailSubscribe` | `0`      |
| `ChatEngine`         | `SIMPLE` |
| `UIThemeStyle`       | `dark`   |

## Building

The minified files (`phone.min.js`, `phone.min.css`) are generated from `phone.js` and `phone.css` using [terser](https://github.com/terser/terser) and [clean-css](https://github.com/clean-css/clean-css-cli).

Install dependencies (requires Node.js):
```
npm install
```

Build both files:
```
npm run build
```

Or build individually:
```
npm run build:js   # phone.js → phone.min.js
npm run build:css  # phone.css → phone.min.css
```

## Testing
```
cd Phone && python3 -m http.server 9000
```
