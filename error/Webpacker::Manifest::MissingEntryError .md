Webpacker::Manifest::MissingEntryError in Users#new
Showing /home/ubuntu/environment/practice/rails_practice_for_beginner_template/app/views/layouts/application.html.erb where line #10 raised:

Webpacker can't find application.js in /home/ubuntu/environment/practice/rails_practice_for_beginner_template/public/packs/manifest.json. Possible causes:
1. You want to set webpacker.yml value of compile to true for your environment
   unless you are using the `webpack -w` or the webpack-dev-server.
2. webpack has not yet re-run to reflect updates.
3. You have misconfigured Webpacker's config/webpacker.yml file.
4. Your webpack configuration is not creating a manifest.
Your manifest contains:
{
}


正しいwebpacker.ymlをセットして
アップデートがまだ
webpacker.yml 構築っミス
マニフェストが作られていません。

yarnをインストールして
$ source <(curl -sL https://cdn.learnenough.com/yarn_install)
webpackerをインストール
rails webpacker:install

--221231