$ bundle exec rspec
/home/ubuntu/.rvm/rubies/ruby-2.7.2/lib/ruby/2.7.0/net/protocol.rb:66: warning: already initialized constant Net::ProtocRetryError
/home/ubuntu/.rvm/gems/ruby-2.7.2/gems/net-protocol-0.2.1/lib/net/protocol.rb:68: warning: previous definition of ProtocRetryError was here
/home/ubuntu/.rvm/rubies/ruby-2.7.2/lib/ruby/2.7.0/net/protocol.rb:206: warning: already initialized constant Net::BufferedIO::BUFSIZE
/home/ubuntu/.rvm/gems/ruby-2.7.2/gems/net-protocol-0.2.1/lib/net/protocol.rb:214: warning: previous definition of BUFSIZE was here
/home/ubuntu/.rvm/rubies/ruby-2.7.2/lib/ruby/2.7.0/net/protocol.rb:503: warning: already initialized constant Net::NetPrivate::Socket
/home/ubuntu/.rvm/gems/ruby-2.7.2/gems/net-protocol-0.2.1/lib/net/protocol.rb:541: warning: previous definition of Socket was here
*****************F.FFFFFFF**

Pending: (Failures listed here are expected and do not affect your suite's status)

  1) Admin::BaseHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/admin/base_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/admin/base_helper_spec.rb:14

  2) Admin::QuestionsHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/admin/questions_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/admin/questions_helper_spec.rb:14

  3) Admin::SessionsHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/admin/sessions_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/admin/sessions_helper_spec.rb:14

  4) Admin::UsersHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/admin/users_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/admin/users_helper_spec.rb:14

  5) AnswersHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/answers_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/answers_helper_spec.rb:14

  6) QuestionsHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/questions_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/questions_helper_spec.rb:14

  7) SessionsHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/sessions_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/sessions_helper_spec.rb:14

  8) UsersHelper add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/helpers/users_helper_spec.rb
     # Not yet implemented
     # ./spec/helpers/users_helper_spec.rb:14

  9) Answer add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/models/answer_spec.rb
     # Not yet implemented
     # ./spec/models/answer_spec.rb:4

  10) Question add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/models/question_spec.rb
     # Not yet implemented
     # ./spec/models/question_spec.rb:4

  11) User add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/models/user_spec.rb
     # Not yet implemented
     # ./spec/models/user_spec.rb:4

  12) Admin::Bases GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/admin/base_spec.rb
     # Not yet implemented
     # ./spec/requests/admin/base_spec.rb:5

  13) Admin::Questions GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/admin/questions_spec.rb
     # Not yet implemented
     # ./spec/requests/admin/questions_spec.rb:5

  14) Admin::Sessions GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/admin/sessions_spec.rb
     # Not yet implemented
     # ./spec/requests/admin/sessions_spec.rb:5

  15) Admin::Users GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/admin/users_spec.rb
     # Not yet implemented
     # ./spec/requests/admin/users_spec.rb:5

  16) Answers GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/answers_spec.rb
     # Not yet implemented
     # ./spec/requests/answers_spec.rb:5

  17) Questions GET /index add some examples (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/requests/questions_spec.rb
     # Not yet implemented
     # ./spec/requests/questions_spec.rb:5

  18) sessions/new.html.erb add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/views/sessions/new.html.erb_spec.rb
     # Not yet implemented
     # ./spec/views/sessions/new.html.erb_spec.rb:4

  19) users/new.html.erb add some examples to (or delete) /home/ubuntu/environment/practice/rails_practice_for_beginner_template/spec/views/users/new.html.erb_spec.rb
     # Not yet implemented
     # ./spec/views/users/new.html.erb_spec.rb:4


Failures:

  1) Sessions GET /new returns http success
     Failure/Error: get "/sessions/new"
     
     ActionController::RoutingError:
       No route matches [GET] "/sessions/new"
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/railties-6.1.7/lib/rails/rack/logger.rb:37:in `call_app'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/railties-6.1.7/lib/rails/rack/logger.rb:26:in `block in call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/railties-6.1.7/lib/rails/rack/logger.rb:26:in `call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/rack-2.2.5/lib/rack/method_override.rb:24:in `call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/rack-2.2.5/lib/rack/runtime.rb:22:in `call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/rack-2.2.5/lib/rack/sendfile.rb:110:in `call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/railties-6.1.7/lib/rails/engine.rb:539:in `call'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/rack-test-2.0.2/lib/rack/test.rb:358:in `process_request'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/rack-test-2.0.2/lib/rack/test.rb:155:in `request'
     # ./spec/requests/sessions_spec.rb:6:in `block (3 levels) in <main>'

  2) 質問から回答までの一連の流れ 基本的な操作 質問から回答までの一連の流れが正しく行われること
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  3) 質問から回答までの一連の流れ ステータスによる質問の絞り込み 質問の「全て」「未解決」「解決済み」の絞り込みが正しく行えること
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  4) 質問から回答までの一連の流れ ページング ページングが実装されていること
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  5) 質問から回答までの一連の流れ 質問, 回答時のメール通知 質問があった際に全員に対して質問があった旨をメールで通知する。（ただし自分は除く）
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  6) 質問から回答までの一連の流れ 質問, 回答時のメール通知 質問に対して回答があった場合は質問者および当該質問に回答したユーザーに対してメールで通知する。（ただし自分は除く）
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  7) サインアップ, サインイン サインアップ サインアップができること
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

  8) サインアップ, サインイン サインイン サインインができること
     Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:21:in `location'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chrome_finder.rb:10:in `version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:51:in `browser_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:142:in `browser_build_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:32:in `latest_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:122:in `download_version'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:134:in `correct_binary?'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/common.rb:91:in `update'
     # /home/ubuntu/.rvm/gems/ruby-2.7.2/gems/webdrivers-5.2.0/lib/webdrivers/chromedriver.rb:156:in `block in <main>'
     # ./spec/support/capybara.rb:4:in `block (2 levels) in <main>'

Finished in 5.14 seconds (files took 2.68 seconds to load)
28 examples, 8 failures, 19 pending

Failed examples:

rspec ./spec/requests/sessions_spec.rb:5 # Sessions GET /new returns http success
rspec ./spec/system/question_answer_spec.rb:6 # 質問から回答までの一連の流れ 基本的な操作 質問から回 答までの一連の流れが正しく行われること
rspec ./spec/system/question_answer_spec.rb:73 # 質問から回答までの一連の流れ ステータスによる質問の 絞り込み 質問の「全て」「未解決」「解決済み」の絞り込みが正しく行えること
rspec ./spec/system/question_answer_spec.rb:99 # 質問から回答までの一連の流れ ページング ページングが実装されていること
rspec ./spec/system/question_answer_spec.rb:118 # 質問から回答までの一連の流れ 質問, 回答時のメール通知 質問があった際に全員に対して質問があった旨をメールで通知する。（ただし自分は除く）
rspec ./spec/system/question_answer_spec.rb:133 # 質問から回答までの一連の流れ 質問, 回答時のメール通知 質問に対して回答があった場合は質問者および当該質問に回答したユーザーに対してメールで通知する。（ただし自分は除く）
rspec ./spec/system/signup_signin_spec.rb:6 # サインアップ, サインイン サインアップ サインアップがで きること
rspec ./spec/system/signup_signin_spec.rb:22 # サインアップ, サインイン サインイン サインインができること


# そもそも
ローカル環境ではなくCloud9で開発していることが原因で発生しているとみた
```
Failure/Error:
       driven_by :selenium, using: :headless_chrome, screen_size: [1000, 600] do |driver_options|
         driver_options.add_argument('--disable-dev-sim-usage')
         driver_options.add_argument('--no-sandbox')
       end
     
     Webdrivers::BrowserNotFound:
       Failed to determine Chrome binary location.
```
https://tech-essentials.work/questions/87

https://qiita.com/jnchito/items/f03934e8db01aec7cdc8

https://steemit.com/japanese/@kakel/aws-cloud9-selenium-headless-chrome-python3

https://teratail.com/questions/195078

# 必要そうな知識
seleniumとは
headlessとは
chromeをcloud９に入れるとは

# selenium install
https://www.manajob.jp/python/python-scraping-2/selenium-installation
https://qiita.com/casareal_user/items/0f8ef4e7cd954a7f6846
https://steemit.com/japanese/@kakel/aws-cloud9-selenium-headless-chrome-python3

`$ curl https://intoli.com/install-google-chrome.sh | bash`