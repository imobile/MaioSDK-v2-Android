# maio SDK v2

- SDK Version: 2.0.7
- 対応 Android Version: 4.4 以降
- Supported Formats: Rewarded/Interstitial/Banner

## What is maio?

[maio](https://adpf-info.i-mobile.co.jp/) はこれまでのバナー広告に加え、新たな広告収益の機会を得ることが可能な動画広告プラットフォームです。
バナー広告と違い、デベロッパーの設定したタイミングで、動画広告をコンテンツの一部として配信することができます。

また、動画広告再生後にアプリ内通貨やライフ等の報酬（リワード）をユーザーに還元する事で、動画広告の再生数が増加し、収益の最大化が見込めます。
今までユーザーが離脱していたポイントに `動画広告 + リワード` を入れる事で、ユーザーのストレスを解消しアクティブ率を向上させる事も可能です。


## Quick Start

### maio SDKの取得

バージョンカタログを使用しない場合/For kotlin projects not using version catalogs:

- maioを導入したいプロジェクトの`build.gradle`に、以下のmavenリポジトリを追加します。
- Add maio Maven repository to your Project build.gradle:

<pre><code>allprojects {
    repositories {
        maven{
            url "https://imobile-maio.github.io/maven"
        }
        google()
        jcenter()
    }
}
</pre></code>

- maioSDKとGoogle Play Servicesをモジュールの`build.gradle`に追加します：
- Add the maio SDK and Google Play Services to your project by adding the following implementations inside your Module build.grade:

### jar 

<pre><code>dependencies {
    implementation 'com.maio:android-sdk-v2:2.0.7'
    implementation 'com.google.android.gms:play-services-ads-identifier:17.0.0'
}
</pre></code>

### aar

<pre><code>dependencies {
    implementation 'com.maio:android-sdk-v2:2.0.7@aar'
    implementation 'com.google.android.gms:play-services-ads-identifier:17.0.0'
}
</pre></code>

 バージョンカタログを使用する場合/For kotlin projects using version catalogs:

- maioを導入したいプロジェクトの`settings.gradle.kts`に、以下のmavenリポジトリを追加します。
- Add maio Maven repository to your Project settings.gradle.kts:

<pre><code>dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven{
            url = uri("https://imobile-maio.github.io/maven")
        }
    }
}
</pre></code>


- maioを導入したいプロジェクトの`libs.versions.toml`に、以下のmavenリポジトリを追加します。
- Add maio Maven repository to your Project libs.versions.toml:

<pre><code>[versions]
maioSdk = "2.0.7"
playServicesAdsIdentifier = "17.0.0"

[libraries]
maio_android_sdk = { group = "com.maio", name = "android-sdk-v2", version.ref = "maioSdk" }
google_play_services_ads_identifier = { group = "com.google.android.gms", name = "play-services-ads-identifier", version.ref = "playServicesAdsIdentifier" }
</pre></code>


- maioSDKとGoogle Play Servicesをモジュールの`build.gradle`に追加します：
- Add the maio SDK and Google Play Services to your project by adding the following implementations inside your Module build.grade:

### jar 

<pre><code>dependencies {
   implementation(libs.google.play.services.ads.identifier)
    implementation(libs.maio.android.sdk)
}
</pre></code>

### aar

<pre><code>dependencies {
   implementation(libs.google.play.services.ads.identifier)
   implementation(libs.maio.android.sdk) {
    artifact {
        type = "aar"
    }
}
}
</pre></code>

## Rewarded の読み込み

<pre><code>
    private fun rewardedLoad(zoneId: String, testMode: Boolean) {
        val request = MaioRequest(zoneId, testMode)
        val rewarded = Rewarded.loadAd(request, applicationContext, object : IRewardedLoadCallback {
            override fun loaded(rewarded: Rewarded) {
                
            }

            override fun failed(rewarded: Rewarded, errorCode: Int) {
            
            }
    })
</pre></code>


## Rewarded の表示

<pre><code>
    private fun rewardedShow() {
        rewarded.show(applicationContext, object : IRewardedShowCallback {
            override fun opened(rewarded: Rewarded) {
         
            }

            override fun closed(rewarded: Rewarded) {
     
            }

            override fun clicked(rewarded: Rewarded) {

            }

            override fun rewarded(rewarded: Rewarded, rewardData: RewardData) {
 
            }

            override fun failed(rewarded: Rewarded, errorCode: Int) {

            }
        })
    }
</pre></code>

## maio SDK Manifest Settings

- maioアクティビティをマニフェストに追加します (aarの場合に必要ありません）：
- Add the maio activity to your manifest (not needed when using aar):

  ```xml 
        <activity
            android:name="AdActivity"
            android:configChanges="orientation|screenLayout|screenSize"
            android:hardwareAccelerated="true"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
        </activity>
        <activity
            android:name="PlayableActivity"
            android:configChanges="orientation|screenLayout|screenSize"
            android:hardwareAccelerated="true"
            android:theme="@android:style/Theme.NoTitleBar.Fullscreen" >
        </activity>
     ```
    
## Manual Download

[releases](https://github.com/imobile/MaioSDK-v2-Android/releases)
から最新のリリースバージョンをダウンロードして下さい。

## Contact Us

- General
    - https://www.i-mobile.co.jp/inquiry.html
- Technical Trouble Shooting
    - https://maio.jp/techsupport/index.html

## 収集しているデータについて

### 凡例

- [x] 収集有り
- [ ] 収集なし

### 連絡先情報

- [ ] **名前** : 姓や名など
- [ ] **Eメールアドレス** : ハッシュ化されたEメールアドレスを含むが、これに限定しない
- [ ] **電話番号** : ハッシュ化された電話番号を含むが、これに限定しない
- [ ] **所在地** : 自宅住所、物理的な住所、郵送先住所など
- [ ] **ユーザのその他の連絡先情報** : 自宅または所在地

### 健康とフィットネス

- [ ] **健康** : ヘルスケアおよび医療関連のデータ、Clinical Health Records API、HealthKit API、MovementDisorderAPI、ヘルスケア関連の臨床調査、またはユーザーが提供したその他のヘルスケアまたは医療のデータを含むが、これらに限定しない
- [ ] **フィットネス** : フィットネスおよび運動データ、Motion APIおよびFitness APIを含むがこれらに限定しない


### 財務情報

- [ ] **支払い情報** : 支払い方法、支払いカード番号、銀行口座番号など。Appが支払いサービスを利用している場合は、支払い情報はApp外で入力され、あなた（デベロッパ）は支払い情報にアクセスできません。その場合、データは収集されないため、申告する必要はありません。
- [ ] **クレジット情報** : クレジットスコアなど
- [ ] **その他の財務情報** : 給与、収入、資産、負債、その他の財務情報など


### 位置情報

- [ ] **詳細な位置情報** : 小数点以下3桁以上の緯度経度と同等、またはそれよりも高い詳細レベルでの、ユーザーまたはデバイスの場所を示す情報
- [ ] **おおよその場所** 小数点以下3桁以上の緯度経度よりも低い詳細レベルでのユーザーまたはデバイスの場所を示す情報（おおよその位置情報サービスなど）


### 機密情報

- [ ] **機密情報** : 人種または民族情報、性的指向、妊娠または出産に関する情報、障がい、宗教または哲学的信念、労働組合への加入、政治的意見、遺伝情報、または生体情報など


### 連絡先

- [ ] **連絡先** : ユーザーの電話、アドレス帳、ソーシャルグラフ内の連絡先リストなど


### ユーザーコンテンツ

- [ ] **Eメールまたはテキストメッセージ** : Eメールまたはメッセージの件名、送信者、受信者、および内容を含む
- [ ] **写真またはビデオ** : ユーザーの写真またはビデオ
- [ ] **オーディオデータ** : ユーザーの声またはサウンドの録音
- [ ] **ゲームプレイコンテンツ** : ゲーム内でユーザーが生成したコンテンツなど
- [ ] **カスタマーサポート** : カスタマーサポートの依頼中にユーザーが生成したデータ
- [ ] **その他のユーザーコンテンツ** : ユーザーが生成したその他のコンテンツ


### 閲覧履歴

- [ ] **閲覧履歴** : ユーザーが閲覧したコンテンツに関する情報


### 検索履歴

- [ ] **検索履歴** : ユーザーが実行した検索に関する情報


### ID

- [ ] **ユーザーID** : スクリーン名、ハンドル、アカウントID、割り当てられたユーザーID、顧客番号、特定のユーザーやアカウントの識別に利用できるユーザーレベルやアカウントレベルのその他のIDなど
- [x] **デバイスID** : デバイスの広告ID、またはデバイスレベルのその他のIDなど
    - 使用目的: サードパーティ広告アナリティクス
    - トラッキングでの利用: あり


### 購入

- [ ] **購入履歴** : アカウントや個人による購入、または購入傾向


### 使用状況データ

- [ ] **製品の操作** : Appの起動、タップ、クリック、スクロール情報、音楽の視聴データ、ビデオの視聴数、ゲームやビデオや曲の保存場所、ユーザーのApp操作に関するその他の情報など
- [x] **広告データ** : ユーザーが見た広告に関する情報など
    - 使用目的: サードパーティ広告アナリティクス
    - トラッキングでの利用: あり
- [ ] **その他の使用状況データ** : Appのユーザーアクティビティに関するその他のデータ


### 診断

- [ ] **クラッシュデータ** : クラッシュログなど
- [ ] **パフォーマンスデータ** : 起動時間、ハング率、エネルギー使用量など
- [ ] **その他の診断データ** : Appに関連する技術的診断を測定する目的で収集されたその他のデータ


### その他のデータ

- [x] **その他の種類のデータ** : 言及されていないその他の種類のデータ
    - 使用目的: サードパーティ広告アナリティクス
    - トラッキングでの利用: あり

### 収集したデータの個人情報への関連付け

収集したデータの個人情報への関連付けを行なっていない。
