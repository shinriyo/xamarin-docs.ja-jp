---
title: "バック グラウンドで実行するアプリケーションを登録します。"
ms.topic: article
ms.prod: xamarin
ms.assetid: 8F89BE63-DDB5-4740-A69D-F60AEB21150D
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 03/18/2017
ms.openlocfilehash: 5fcb41f4f60adc8ca5be761c2b9a7449387a89d0
ms.sourcegitcommit: 30055c534d9caf5dffcfdeafd6f08e666fb870a8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2018
---
# <a name="registering-applications-to-run-in-the-background"></a>バック グラウンドで実行するアプリケーションを登録します。

一部のアプリケーションが GPS 経由でユーザーの方向を取得するなど、重要な実行時間の長いタスクを実行時にアプリケーションが常に呼び出された場合の動作のバック グラウンド特権 works の個々 のタスクを登録しますか。 次のようのアプリケーションは、既知の必要なバック グラウンド アプリケーションとして代わりに登録する必要があります。

アプリを登録する信号を iOS こと、アプリケーションがバック グラウンドでタスクを実行するために必要な特別な特権を指定してください。

## <a name="application-registration-categories"></a>アプリケーション登録のカテゴリ

登録済みのアプリは、いくつかのカテゴリに分類できます。

-  **オーディオ**-続行ミュージック プレーヤーやオーディオ コンテンツを使用する他のアプリケーションを登録することがありますも、アプリが不要になった、フォア グラウンドでオーディオを再生します。 IOS は、アプリは、このカテゴリでは、オーディオを再生またはバック グラウンドでダウンロード以外は何も操作しようとすると、これが終了されます。
-  **VoIP** -バック グラウンドでのオーディオの処理を保持するオーディオのアプリケーションに与えられている同じ特権の音声経由で (Voip) アプリケーションを取得します。 電源をその接続を維持する VoIP サービスに必要に応じて応答にも使用します。
-  **外部のアクセサリおよび Bluetooth** -Bluetooth デバイスとその他のハードウェアが外部アクセサリと通信する必要があるアプリケーション用に予約されて、これらのカテゴリの下の登録、アプリに許可ハードウェアへの接続を維持します。
-  **Newsstand** -A Newsstand アプリケーションは引き続きバック グラウンドでコンテンツを同期します。
-  **場所**- を行うアプリケーション、GPS のまたはネットワークの場所のデータが送信し、バック グラウンドでの場所の更新プログラムを受信します。
-  **フェッチ (iOS 7 以降)** - アプリケーションがバック グラウンド fetch 権限は提示してきたユーザー更新されたコンテンツをアプリケーションに戻るときに、定期的に新しいコンテンツのプロバイダーを確認することができますを登録します。
-  **リモート通知 (iOS 7 以降)** -アプリケーションが通知を受信する、プロバイダーからの登録をユーザーがアプリケーションを開く前に、更新プログラムを開始する通知を使用します。 通知では、プッシュ通知の形式で取得したり、アプリケーションを自動的にスリープ解除することを選択することができます。


設定してアプリケーションを登録することができます、**バック グラウンド モードのために必要な**アプリケーションのプロパティ*Info.plist*です。 必要な数のカテゴリにアプリケーションを登録できます。

 [![](registering-applications-to-run-in-background-images/bgmodes.png "バック グラウンド モードを設定")](registering-applications-to-run-in-background-images/bgmodes.png#lightbox)

バック グラウンドの場所の更新プログラムのアプリケーションを登録する手順については、次を参照してください。、[背景場所チュートリアル](~/ios/app-fundamentals/backgrounding/ios-backgrounding-walkthroughs/location-walkthrough.md)です。

## <a name="application-does-not-run-in-background-property"></a>アプリケーションは、バック グラウンド プロパティでは実行できません。

別のプロパティで設定できる*Info.plist*は、*アプリケーションがバック グラウンドで実行されない*、または`UIApplicationExitsOnSuspend`プロパティ。

 [![](registering-applications-to-run-in-background-images/plist.png "実行しているバック グラウンドの無効化")](registering-applications-to-run-in-background-images/plist.png#lightbox)

この、正確な背景アプリの更新設定を iOS 7 以降では、開発者側でのみ変更できます点を除いてオフに設定と同じ効果があり ios 4 および上で利用できます。 アプリケーションでは、バック グラウンドでの入力の直後後が中断され、処理を実行することはできません。

予期しない動作を防ぐことと、バック グラウンド処理を処理するアプリケーションが設計されていない場合は、このプロパティを使用します。

## <a name="background-fetch-and-remote-notifications"></a>バック グラウンドでフェッチとリモートの通知

バック グラウンドでフェッチとリモートの通知には特別な登録カテゴリが iOS 7 で導入されました。 これらのカテゴリでは、アプリケーション、プロバイダーから新しいコンテンツを受信し、バック グラウンドで更新をできるようにします。 次のセクションでは、フェッチおよび詳しくは、リモートの通知について説明しも iOS 6 でバック グラウンドでアプリケーションを更新するための手段として、位置情報を紹介します。
