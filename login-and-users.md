<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Login and users</title>
  <base href="./login and users.html">
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
  <link rel="stylesheet" href="./mobile.css" />
  <link rel="stylesheet" href="https://fonts.googleapis.com/icon?family=Material+Icons">
  <link rel="shortcut icon" href="./favicon.ico" type="image/x-icon">
  
  <meta property="og:url"                content="https://mytee306.github.io/blog/login and users.html" />
  <meta property="og:type"               content="article" />
  <meta property="og:title"              content="Login and users" />
  <meta property="og:description"        content="Read full article at https://mytee306.github.com/blog/login and users.html" />
  <meta property="og:image"              content="https://imgur.com/G3CgjIK.png" />
  <meta property="og:image:width" content="125" />
  <meta property="og:image:height" content="125" />
  
  <meta name="twitter:card" content="summary" />
  <meta name="twitter:site" content="https://mytee306.github.io/blog/login and users.html" />
  <meta name="twitter:title" content="Login and users" />
  <meta name="twitter:description" content="Read full article at https://mytee306.github.com/blog/login and users.html" />
  <meta name="twitter:image" content="https://imgur.com/G3CgjIK.png" />
</head>

<body class="stackedit">
  <div class="toc__toggle" tabindex="0">
    <i class="material-icons">toc</i>
  </div>
  
  <div class="stackedit__left app-hidden">
    <div class="stackedit__toc">
      
<ul>
<li>
<ul>
<li><a href="#folder-structure">Folder structure</a></li>
<li><a href="#components">Components</a></li>
<li><a href="#storybook">Storybook</a></li>
<li><a href="#state">State</a></li>
<li><a href="#epics">Epics</a></li>
<li><a href="#questions">Questions</a></li>
</ul>
</li>
</ul>

    </div>
  </div>
  <div class="stackedit__right">
    <div class="stackedit__html">
      <h2 id="folder-structure">Folder structure</h2>
<h3 id="modules">modules</h3>
<p>anything redux related</p>
<h4 id="mappers--decoders-">mappers ( decoders )</h4>
<p>For mapping <em>raw</em> <code>http response</code> objects</p>
<h2 id="components">Components</h2>
<p>packages\foleon-account\src\components\privilege-listener\privilege-listener.tsx<br>
packages\foleon-account\docs\<a href="http://privilege-listener-component.md">privilege-listener-component.md</a></p>
<h2 id="storybook">Storybook</h2>
<h3 id="login">Login</h3>
<p>All components</p>
<h3 id="account">Account</h3>
<p>N / A</p>
<h2 id="state">State</h2>
<p>privileges<br>
…<br>
account<br>
users<br>
<code>error</code> field but no <code>loading</code> field</p>
<hr>
<h2 id="epics">Epics</h2>
<h3 id="login-1">Login</h3>
<p>packages\foleon-login\src\modules\epics.ts<br>
packages\foleon-login\src\modules\login\epics.ts</p>
<h3 id="logout">Logout</h3>
<h4 id="clearing-redux-state">Clearing redux state</h4>
<pre class=" language-ts"><code class="prism  language-ts">window<span class="token punctuation">.</span>location<span class="token punctuation">.</span><span class="token function">reload</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h3 id="account-1">Account</h3>
<p>packages\foleon-account\src\modules\epics.ts</p>
<h4 id="auth-state--fetchme-">Auth State ( fetchMe )</h4>
<p><code>packages/foleon-account/src/modules/epics.ts :53</code></p>
<pre class=" language-ts"><code class="prism  language-ts"><span class="token function">takeWhile</span><span class="token punctuation">(</span><span class="token punctuation">(</span>response<span class="token punctuation">:</span>  User<span class="token punctuation">.</span>IRawMe<span class="token punctuation">)</span> <span class="token operator">=&gt;</span>  <span class="token keyword">typeof</span>  response<span class="token punctuation">.</span>id  <span class="token operator">===</span>  <span class="token string">'number'</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
</code></pre>
<h3 id="helpers">Helpers</h3>
<p>packages\foleon-account\src\modules\helpers.ts @addEntityAndSetCurrent</p>
<h3 id="logout-1">Logout</h3>
<pre><code>
switchMap(() =&gt; { // same as mergeMap
  window.location.reload();
  return  empty();
})


</code></pre>
<hr>
<h2 id="questions">Questions</h2>
<h3 id="overkill-operators">Overkill operators</h3>
<pre class=" language-ts"><code class="prism  language-ts"><span class="token function">concatMap</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=&gt;</span>  <span class="token keyword">of</span><span class="token punctuation">(</span><span class="token function">hyadrateAccessTokenHelper</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token comment">/*
same as map(() =&gt;  hyadrateAccessTokenHelper())
*/</span>
</code></pre>
<h3 id="unhandled-error-actions">Unhandled error actions</h3>
<p>unhandled error actions<br>
FETCH_PRIVILEGES_FAILED<br>
FETCH_ME_FAILED</p>
<h3 id="older-version-of-rxjs">Older version of rxjs</h3>
<p>rxjs@5.5.12</p>
<h3 id="isactionof-vs-oftype">isActionOf vs ofType</h3>

    </div>
  </div>
  
  <script src="./index.js"></script>
  <!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=UA-137872597-1"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'UA-137872597-1');
  </script>
</body>

</html>
