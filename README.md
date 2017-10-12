# play dockerのテンプレート

## 準備
sbtに以下を追加するだけでおk
```
maintainer in Docker := "author"
dockerExposedPorts in Docker := Seq(9000, 9443)
``

## 実行
```sbt docker:publishLocal```でbuild.sbtのnameとversionに合わせた名前でdockerイメージが作成される。
でdocker run
```$ docker run --net=host [作成したイメージ]```

## Generating an application secret
以下のコマンでkey取得

sbt playGenerateSecret

application.conf内に以下を追加

```
play.crypto.secret="changeme"
play.crypto.secret="生成されたキー"
```

