---
title: "ネイティブ型"
ms.topic: article
ms.prod: xamarin
ms.assetid: B5237770-0FC3-4B01-9E22-766B35C9A952
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
ms.date: 01/25/2016
ms.openlocfilehash: 09858bd7902b44bbedd96f1be9c9c827131ee16f
ms.sourcegitcommit: 5fc1c4d17cd9c755604092cf7ff038a6358f8646
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/17/2018
---
# <a name="native-types"></a>ネイティブ型

Mac と iOS Api の両方は、差の中核には、32 ビット プラットフォームでは 32 ビットと 64 ビットの 64 ビット プラットフォームでは、常に、アーキテクチャ固有のデータ型を使用します。

Objective C のたとえば、マップ、`NSInteger`のデータ型`int32_t`32 ビット システム上に`int64_t`64 ビット システムでします。

以前の使用を置き換える、統合 API では、この動作を一致するように`int`(として常に定義されている .net `System.Int32`) を新しいデータ型:`System.nint`です。  考えることができます"n"の意味「ネイティブ」プラットフォームのネイティブの整数を入力するようにします。

これらの新しいデータ型での 32 ビット、32 ビットおよび 64 ビットまたは 64 ビット、コンパイル フラグによって、同じソース コードがコンパイルされます。

## <a name="new-data-types"></a>新しいデータ型

次の表は、この新しい 32/64 ビット環境を一致するように、データ型で変更を示しています。

|ネイティブ型|32 ビットのバッキング型|64 ビットのバッキング型|
|--- |--- |--- |
|`System.nint`|`System.Int32` (`int`)|`System.Int64` (`long`)|
|`System.nuint`|`System.UInt32` (`uint`)|`System.UInt64` (`ulong`)|
|`System.nfloat`|`System.Single` (`float`)|`System.Double` (`double`)|

今日の見た目と同じ方法で検索増減する c# コードを許可するには、その名前を選択しました。

### <a name="implicit-and-explicit-conversions"></a>暗黙の型変換と明示的な型変換

新しいデータ型のデザインは、単一 c# ソース ファイルをホスト プラットフォームとコンパイルの設定によって 32 ビットまたは 64 ビットのストレージが必然的に使用を許可するものです。

これは、.NET の整数と浮動小数点データ型への明示的および暗黙的な変換プラットフォームに固有のデータ型とのセットを設計するために必要です。

(32 ビットの値を 64 ビットの場所に格納されている) のデータ損失の可能性がない場合に、暗黙的な変換演算子が提供されます。

データ損失の可能性がある場合に、明示的な変換の演算子を指定 (します 64 ビット値は 32 ビットまたは 32 可能性のある記憶域の場所に格納されている)。

 `int`、`uint`と`float`すべてに暗黙的に変換`nint`、`nuint`と`nfloat`32 ビットに常に 32 ビットまたは 64 ビットに収まるようにします。

 `nint`、`nuint`と`nfloat`はすべてに暗黙的に変換`long`、`ulong`と`double`32 ビットまたは 64 ビットの値は、64 ビットの記憶域に常に収まるようにします。

明示的な変換を使用する必要があります`nint`、`nuint`と`nfloat`に`int`、`uint`と`float`のためのネイティブ型は、記憶域の 64 ビットを保持可能性があります。

明示的な変換を使用する必要があります`long`、`ulong`と`double`に`nint`、`nuint`と`nfloat`ネイティブ型は記憶域の 32 ビットを保持することのみされる可能性があります。

## <a name="coregraphics-types"></a>CoreGraphics 型

CoreGraphics で使用されるポイント、サイズ、および四角形のデータ型で実行されているデバイスに応じて 32 ビットまたは 64 ビットを使用します。  ホストのプラットフォームのサイズを一致するように発生した既存のデータ構造を使用してもともとバインドされている場合、iOS と Mac Api (データ型`System.Drawing`)。

移動するときに**統合**のインスタンスを置換する必要があります`System.Drawing`でその`CoreGraphics`次の表に示すように対応します。

|System.Drawing の古い型|新しいデータ型 CoreGraphics|説明|
|--- |--- |--- |
|`RectangleF`|`CGRect`|浮動小数点を保持では、四角形の情報をポイントします。|
|`SizeF`|`CGSize`|浮動小数点を保持ポイント サイズの情報 (幅、高さ)|
|`PointF`|`CGPoint`|浮動小数点を保持ポイント情報 (X, Y)|

データ構造体の要素を格納する古いデータ型を使用する浮動小数点の値が 1 つを使用して新しい while`System.nfloat`です。

## <a name="related-links"></a>関連リンク

- [クロスプラットフォーム アプリでのネイティブ型の使用](~/cross-platform/macios/native-types-cross-platform.md)
- [従来の vs Unified API の相違点](https://developer.xamarin.com/releases/ios/api_changes/classic-vs-unified-8.6.0/)
