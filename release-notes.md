# Release Notes

## v1.2.4 (2016-12-22)
- iOS7以下において、広告からストアに遷移した場合、アプリに戻っても操作できなくなる不具合があったため、これを修正。

## v1.2.3 (2016-12-21)
- 内部でダウンロードした広告リソースの検証に一部不具合があったため、これを修正。
- 動画広告の再生準備中、クラッシュする可能性があったので、これを修正。

## v1.2.2 (2016-12-15)
- 動画広告の再生エラーにより広告が閉じられる際にクラッシュする可能性があったので、これを修正。
- スレッドセーフにデザインされたクラス内に一部スレッドセーフでない処理が入っていたので、これを修正。

## v1.2.1 (2016-12-09)
- 動画広告の再生準備に失敗し再生が行われないケースがあったので、これを修正。

## v1.2.0 (2016-12-09)
- ストア遷移時に、アプリ内でストアを開くように変更。

## v1.1.7 (2016-11-09)
- UINavigationController 等から広告を表示すると、広告クローズ時に正しい InterfaceOrientation に戻れない場合があるので、これが端末向きとなるよう修正。
- 同一メディアに多数のゾーンが存在する場合、SDK の初期化に必要以上の時間がかかる事があるので、これを修正。
- [Maio showAtZoneId:vc:] メソッドの vc に渡された値が、v1.1.3 以降 使用されていなかった不具合を修正。

## v1.1.6 (2016-08-25)
- ビルド時に「warning: /var/folders/xxx: No such file or directory」が大量に生じる問題を修正。
- SDK のファイルサイズを最適化。

## v1.1.5 (2016-08-03)
- HTTP ステータス 503 などで無効なメディア情報をダウンロードすると、ダウンロードマネージャの最大同時リクエスト数設定が 0 となり配信サーバへのリクエストが行われなくなる場合があるので、これを修正。
- 動画画面を閉じた後も dealloc が呼ばれず、直ぐに関連リソースが解放されない場合があるので、明示的に解放するよう修正。
- アプリを再起動しないとメモリ上にキャッシュしたメディア情報を使い続ける不具合を修正。
- 一部処理の最適化と、軽微な不具合の修正。

## v1.1.4 (2016-07-28)
- cocos2d-x-3.12 未満では AppDelegate に window プロパティが実装されていない為、"[AppController window]: unrecognized selector" となりクラッシュするので、それを回避。
https://github.com/cocos2d/cocos2d-x/issues/13285

## v1.1.3 (2016-07-15)
- Unity 経由で maio の動画広告を再生完了させた際、アプリをバックグラウンド→フォアグラウンドで遷移させると、エンドカードの裏側で勝手に動画が再開されてしまう不具合を修正。
- UIViewController の存在しない、または window ヒエラルキーに存在しない UIWindow から [Maio show] 系メソッドを呼び出すと、動画広告に遷移できない不具合を修正。（e.g. UIAlertView）
- テスト配信モード(adTestMode=YES)時、SDK セットアップが完了する前に [MaioInstance canShow:] を呼び出すと例外となる不具合を修正。

## v1.1.2 (2016-05-18)
- Apple/Reachability を IPv6 に対応した v5.0 に更新。
- [Test for IPv6 DNS64/NAT64 Compatibility Regularly]に従って動作確認。
- 動画広告の再生準備中に着信割込み等でアプリが非アクティブになると、動画が再生されず操作できなくなってしまう不具合を修正。
- バックグラウンド時に行っていた動画の一時停止処理を非アクティブ時に行うよう修正。
- 動画広告表示中にアプリがバックグラウンドに遷移した際、広告が閉じられるよう制御するオプション機能を実装。

## v1.1.1 (2016-05-06)
- bitcode を含めるよう対応。

## v1.1.0 (2016-05-06)
- 複数の maio Media ID を設定できるよう、クラス構造をリファクタリングし対応。
- 動画再生準備完了時に、次のクリエイティブをプリロードするよう対応。
- 何らかの事由で動画広告が一時停止された際に、画面に再生ボタンを表示するよう対応。
- その他内部挙動・軽微なバグの微修正。

## v1.0.7 (2016-04-29)
- 動画制御 UI ファイルが破損していた場合に、動画が停止し操作できなくなってしまうので、速やかにエラー通知しアプリに戻るよう修正。
- MD5 ハッシュ値によるクリエイティブ検証処理を追加。
- 動画再生中に Siri により割り込まれた後、動画が停止してしまう不具合を修正。
- SDK のバージョンを返すメソッドを追加。

## v1.0.6 (2016-04-15)
- 動画が破損等により再生途中で停止した場合に、再生エラーとして処理されなかった不具合を修正。
- ダウンロードしたクリエイティブリソースが破損していた場合にリトライするよう修正。
- オフラインとオンラインが頻繁に切り替わると、クリエイティブのダウンロードが一時的に停止してしまう不具合を修正。

## v1.0.5 (2016-02-04)
- 動画再生エラー時に動画広告が閉じない不具合を修正。
- info.plist の CFBundleShortVersionString が無い状態で SDK をセットアップするとクラッシュする不具合を修正。

## v1.0.4 (2015-11-25)
- 一枚画像のエンドカード時にオリエンテーションが固定されるよう修正
- iOS9 以降のデバイスから canOpenUrl が呼ばれた際にエラーログが出力されないよう修正
- メインスレッド外から動画広告を再生するとエラーとなる不具合を修正

## v1.0.3 (2015-10-21)
- 動画再生後に、AudioSession の設定が初期化されてしまう不具合を修正
- 回転検出時、UIDeviceOrientationUnknown を正常に処理できていなかったので対応。
- iOS9 から supportedInterfaceOrientations の返値の型が微妙に変わったので修正。

## v1.0.2 (2015-09-01)
- アクティブなクリエイティブキャッシュまで削除されてしまう不具合を修正
- 動画再生毎にメモリリークしてしまう不具合を修正

## v1.0.1 (2015-08-27)
- window.rootViewController 以外の UIViewController から [Maio show] をコールするとエラーとなり広告が表示されない不具合を修正
- 配信優先度の高いキャンペーンが、キャッシュアウトされても優先的に選ばれてしまい、広告が表示されない不具合を修正
- アプリ起動中に動画キャッシュファイルがシステムによって削除されてしまった場合、暫くの間広告表示が行えなくなる不具合を修正

## v1.0.0 (2015-08-21)
