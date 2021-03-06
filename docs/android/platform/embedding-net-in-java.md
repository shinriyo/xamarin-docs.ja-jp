---
title: Java で .NET の埋め込み
description: Java ベースのネイティブ Android プロジェクトでの Xamarin の .NET ライブラリを使用する方法
ms.topic: article
ms.prod: xamarin
ms.assetid: A489EEF3-1008-4257-BF63-FE21D8C23821
ms.technology: xamarin-android
author: mgmclemore
ms.author: mamcle
ms.date: 03/28/2018
ms.openlocfilehash: f0da12d739c6003257d3acf9ccefdec7e36f5349
ms.sourcegitcommit: 17a9cf246a4d33cfa232016992b308df540c8e4f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2018
---
# <a name="embedding-net-in-java"></a>Java で .NET の埋め込み

場合によっては、既存のネイティブの Android プロジェクトに Xamarin .NET ライブラリを追加することがあります。 これを行うには、使用することができます、 [Embeddinator 4000](https://mono.github.io/Embeddinator-4000/)ネイティブ Java ベースの Android アプリに組み込むことがネイティブ ライブラリに .NET ライブラリを有効にするツールです。

 
## <a name="requirements"></a>要件

Embeddinator 4000 を Android で Java を使用するのには、次のものが必要。

-   **Android Studio** &ndash; [Android Studio 3.x](https://developer.android.com/studio/preview/index.html) or later must be installed.

-   **Xamarin.Android** &ndash; [Xamarin.Android 7.5](https://www.visualstudio.com/xamarin/) or later must be installed.

-   **Java Developer Kit** &ndash; [Java 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)以降、インストールする必要があります。

-   **モノラル** &ndash; [モノラル 5.0](http://www.mono-project.com/download/)以降、インストールする必要があります。


# <a name="visual-studiotabvswin"></a>[Visual Studio](#tab/vswin)

Visual Studio を使用して、編集および c# コードをコンパイルすることができます。

# <a name="visual-studio-for-mactabvsmac"></a>[Visual Studio for Mac](#tab/vsmac)

Visual Studio for Mac を使用して、編集および c# コードをコンパイルすることができます。

-----

 
## <a name="using-the-embeddinator-4000"></a>Embeddinator 4000 を使用します。

ネイティブの Android プロジェクトでの .NET ライブラリを使用するのには、次の手順を使用します。

1.  C# での Android ライブラリ プロジェクトを作成します。

2.  NuGet 経由での Embeddinator 4000 をインストールします。

3.  Android ライブラリのアセンブリで Embeddinator を実行します。

4.  Android Studio での Java プロジェクトで生成された AAR ファイルを使用します。

次の手順で詳しく説明は、 [Embeddinator 4000](https://mono.github.io/Embeddinator-4000/getting-started-java-android.html)ドキュメント。
