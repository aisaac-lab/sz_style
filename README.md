# DEV
```ruby
gem 'sz_style', path: '../sz_style'
gem 'font-awesome-rails'
```


```bash
gem 'sz_style', git: 'git@github.com:aisaac-lab/sz_style.git'
gem 'font-awesome-rails'

touch app/views/layouts/admin.html.erb
mkdir -p app/helpers/admin/
cat << EOS > app/helpers/admin/application_helper.rb
module Admin::ApplicationHelper
  def is_active_controller(*controller_names)
    controller_names.each do |controller_name|
      if params[:controller] == controller_name
        break 'active'
      end
    end
  end
end
EOS

mkdir -p app/controllers/admin
cat << EOS > app/controllers/admin/application_controller.rb
class Admin::ApplicationController < ActionController::Base
  layout 'admin'
end
EOS

cat << EOS > app/assets/javascripts/admin.js
  //= require sz_style
EOS

cat << EOS > app/assets/stylesheets/admin.scss
/*
 *= require sz_style
 *= require_self
 */
EOS
```