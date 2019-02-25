## CLIでHerokuが使えるようにする
```bash
cd
curl https://cli-assets.heroku.com/install-ubuntu.sh | sudo sh
heroku login
```
```bash
cd rails_projects/action_stats/
heroku git:remote -a action-stats-server
git subtree push --prefix=server/ heroku master
# リポジトリルートがアプリルートと一致する場合は subtree を使用する必要はない為、pushは以下コマンドで十分
# git push heroku master
```

```bash
# db:create は不要だった
sudo heroku run rake db:migrate
```

## db:migrate:reset の役割
```bash
sudo heroku pg:reset DATABASE_URL
```
confirm オプションを付けると、実行後に「action-stats-server」と打たなくて済むらしい
```bash
sudo heroku pg:reset DATABASE_URL --confirm action-stats-server
```
