$ curl -X POST -F 'article[title]=hoge' -F 'article[content]=fuga' https://41287f2174e541fba1c325c005b3e99f.vfs.cloud9.ap-northeast-1.amazonaws.com/articles
<html>

<head>
    <meta charset='utf-8'>
    <title>
        VFS connection does not exist
    </title>
    <style type="text/css">
        .theme-error{min-height:90vh;padding-bottom:15px;box-sizing:border-box;display:flex;flex-direction:column;}
.middle{text-align:center;font-weight:600;}
.filler{flex:1;}
.text{font-weight:600;font-size:300px;line-height:300px;}
.subtext{font-size:41px;margin-top:50px;}
.info{font-size:24px;font-weight:300;display:inline-block;margin-top:100px;line-height:30px;color:#666666;max-width:1000px;text-align:left;}
.error404 .text{color:#3388DD;}
.error404 .subtext{color:#3388DD;}
.error500 .text{color:#444444;}
.error500 .subtext{color:#444444;}
.error503 .text{color:#E07700}
.error503 .subtext{color:#E07700}

        .extra .theme-error .error_content {
            display: none;
        }
        #-msg {
            display: inline-block;
        }
    </style>
</head>

<body class="extra">
    <div class="theme-error error404">
        <div class="filler"></div>
        <div class="middle">
            <div class="text">Oops</div>
            <div class="subtext">
                VFS connection does not exist
            </div>

            <div class="error_content info" id="project-access-msg">
                <p>Amazon Cloud9 can't get you to your requested environment. Here are some suggestions on how to figure out what's going on:
                    <div class="baseList">
                        <ul>
                            <li>Check that you have access to <a href="undefined/cloud9/ide/41287f2174e541fba1c325c005b3e99f">your environment</a> and are signed into Amazon Cloud9 for the environment.</li>
                            <li>Check that the server is successfully running on Amazon Cloud9:
                                <ul>
                                    <li>If the server hit an error, the output window will have a message telling you what it is.</li>
                                    <li>If you're in the middle of debugging code, your server might be paused right now.</li>
                                    <li>The server might be running on a different port; make sure it runs on port 8080.</li>
                                </ul>
                            </li>
                        </ul>
                    </div>
                </p>
            </div>

            <div class="error_content info" id="ratelimit-msg">
                <p>Too many requests were made through application preview. Please wait a moment before making another request.</p>
            </div>

            <div class="error_content info" id="bad_headers-msg">
                <p>The request could not be proxied because some headers contained invalid data.</p>
            </div>
            
            <div class="error_content" id="generic-msg">
              <p>There was an error proxying the request.</p>
            </div>
        </div>
        <div class="filler"></div>
    </div>
</body>

</html>


## 参考URL
https://qiita.com/atsushi101011/items/c0cc54261ab2f3a7c22c  
https://teratail.com/questions/124827  
