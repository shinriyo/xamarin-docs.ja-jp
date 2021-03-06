---
title: "浮動小数点"
ms.topic: article
ms.prod: xamarin
ms.assetid: 003F25C1-B430-4339-9C95-7DF527EBC699
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.openlocfilehash: 73681a37f15f3dd93c85bafb6bb9d71ab30af85c
ms.sourcegitcommit: 0fdb243b46cf21be47584900805cadcd077121bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="floating-point"></a>浮動小数点

Xamarin.iOS 既定では、ARM 上の 64 ビットの精度を使用して 32 ビットおよび 64 ビットの浮動小数点演算です。  

この精度が高いほどは C# の場合、デスクトップ、モバイル、上での浮動小数点演算から開発者が期待どおりに近いパフォーマンスに与える影響が大きなあります。

32 ビット浮動小数点演算を使用する 32 ビット浮動ポイント コードをコンパイルすることができます。  これを行うには、少なくともを使用する必要があります。 Xamarin.iOS 8.10 とセットを、iOS でビルド オプションのパネル、"mtouch 余分な引数"エントリは、次の値を行。

     --aot-options=-O=float32

これは、静的なコンパイラに通知 (モノラルの組み込み静的コンパイラでは、またはある LLVM 電源 1 のいずれか) を 32 ビットの浮動小数点値を使用して浮動小数点演算を実行します。
