<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__left">
    <div class="stackedit__toc">
<h1>Snapchat-Snapkit-DIY-Docs</h1>
<ul>
<li><a href="#purpose">Purpose</a></li>
<li><a href="#ios-centric">iOS Centric</a></li>
<li><a href="#contributing">Contributing</a></li>
<li><a href="#bugs-and-requests">Bugs and requests</a></li>
<li><a href="#contact">Contact</a></li>
</ul>
</li>
<li><a href="#snapkit">Snapkit</a>
<ul>
<li><a href="#loginkit">LoginKit</a></li>
</ul>
</li>
</ul>

  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h1 id="snapchat-snapkit-diy-docs">Snapchat-Snapkit-DIY-Docs</h1>
<p>Snapchat-Snapkit-DIY-Docs</p>
<h2 id="purpose">Purpose</h2>
<p>Snapchat’s Snapkit is new and there are holes in the documentation.  As developers implement Snapkit, they will develop best practices.  This document exists to help developers obtain success with Snapkit and document the best practices they come across.</p>
<p>There will be copy/paste form the Snapkit documentation.  The purpose of which is to make it easy to see what is there as well as what <strong>should</strong> be there</p>
<h2 id="ios-centric">iOS Centric</h2>
<p>I’m working to integrate Snapkit into an existing iOS Swift project, and so I’ll be adding mostly iOS centric information.  As this repository is open, anyone is welcome to add Android info.</p>
<h2 id="contributing">Contributing</h2>
<p>Please fork and submit pull requests</p>
<h2 id="bugs-and-requests">Bugs and requests</h2>
<p>File bugs or requests as any other repository.  Feel free to work on anything that is there.</p>
<h2 id="contact">Contact</h2>
<p>For most things, file bugs.  anything else:<br>
@saganoneapps on twitter</p>
<h1 id="snapkit">Snapkit</h1>
<h2 id="loginkit"><a href="https://docs.snapchat.com/docs/login-kit/">LoginKit</a></h2>
<h3 id="getting-started">Getting started</h3>
<p>In your app project in Xcode, add SCSDKCoreKit.framework and SCSDKLoginKit.framework into General &gt; Embedded Binaries.</p>
<p>Add the following fields in your application’s Info.plist file:</p>
<ul>
<li>SCSDKClientId (string): Your application’s client ID</li>
</ul>
<p>…<br>
It isn’t clear what <strong>client ID</strong> means.  The documentation immediately before this says</p>
<blockquote>
<p>Requirements<br>
Client ID from the developer portal<br>
iOS version 10.0+</p>
</blockquote>
<p>However, there is absolutely nothing in the developer portal with a lable <strong>client ID</strong>.  Do they mean OAUTH CLIENT ID?  (I suspect so, but have an email out to them asking about this)<br>
…</p>
<ul>
<li>SCSDKRedirectUrl (string): The URL that will handle and complete login requests; must be a valid URL in the form foo://bar — without bar, redirects will fail</li>
</ul>
<p>…<br>
Translating the above into English/code …<br>
So if you registered my-app://auth/snap then you would have this entry in your Info.plist:</p>
<pre class=" language-xml"><code class="prism  language-xml"><span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>key</span><span class="token punctuation">&gt;</span></span>SCSDKRedirectUrl<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>key</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>string</span><span class="token punctuation">&gt;</span></span>my-app://auth/snap<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>string</span><span class="token punctuation">&gt;</span></span>
<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>key</span><span class="token punctuation">&gt;</span></span>CFBundleURLTypes<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>key</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>array</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>dict</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>key</span><span class="token punctuation">&gt;</span></span>CFBundleTypeRole<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>key</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>string</span><span class="token punctuation">&gt;</span></span>Editor<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>string</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>key</span><span class="token punctuation">&gt;</span></span>CFBundleURLSchemes<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>key</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>array</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;</span>string</span><span class="token punctuation">&gt;</span></span>my-app<span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>string</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>array</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>dict</span><span class="token punctuation">&gt;</span></span>
 <span class="token tag"><span class="token tag"><span class="token punctuation">&lt;/</span>array</span><span class="token punctuation">&gt;</span></span>
</code></pre>
<ul>
<li>See this <a href="https://github.com/Snap-Kit/bitmoji-sample/blob/master/ios/BitmojiSampleApp/Supporting%20Files/Info.plist">sample info.plist</a> from Snapchat</li>
<li>See this <a href="https://medium.com/adventures-in-ios-mobile-app-development/snapchat-snapkit-developer-support-sadly-sad-89d63011c6ad">medium post</a></li>
<li>See this <a href="https://github.com/Snap-Kit/bitmoji-sample/issues/3">bug filed</a><br>
…</li>
</ul>
  </div>
  <h1>Snapchat Snapkit Support</h1>
  <p>Want support?  In theory go to <a href="https://support.snapchat.com/en-US/i-need-help">I need help</a>
  <p>Do not do what the documentation says to do in order to get support.  This is the doc:</p>
  <img src="https://i.imgur.com/ftE1pUt.png">
  <p>But this is the response I got from doing exactly what it says to do:<p>
  <img src="https://i.imgur.com/jm0ED31.png">
</body>

</html>
