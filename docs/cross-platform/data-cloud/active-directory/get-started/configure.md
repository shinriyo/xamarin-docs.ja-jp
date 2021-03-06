---
title: "手順 2. モバイル アプリケーションのサービスへのアクセスを構成します。"
ms.topic: article
ms.prod: xamarin
ms.assetid: 8A14A457-F72E-4B08-B4B6-801F7619F893
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
ms.date: 03/23/2017
ms.openlocfilehash: a679d404eace121b38463e35350b8b85ec08b1e0
ms.sourcegitcommit: 6cd40d190abe38edd50fc74331be15324a845a28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="step-2-configure-service-access-for-mobile-application"></a>手順 2. モバイル アプリケーションのサービスへのアクセスを構成します。

任意リソース web アプリケーションなど、web サービスなど、Azure Active Directory によってセキュリティで保護する必要があるときに、登録する必要があります。 すべてのセキュリティで保護されたアプリケーションまたはサービスを確認できます**アプリケーション**タブです。ここでモバイル アプリケーションからアクセスして、それにアクセスできるようにする必要があるアプリケーションを選択できます。

1. **構成** タブで、検索**他のアプリケーションに対するアクセス許可**セクション。

  ![](configure-images/2.1-configure.png "[構成] タブで、その他のアプリケーション セクションへのアクセス許可を見つける")

2.  をクリックして**アプリケーションの追加**ボタンをクリックします。 ポップアップの次の画面では、Azure Active Directory によってセキュリティで保護されたすべてのアプリケーションの一覧が表示されます。 モバイル アプリケーションからアクセスする必要があるアプリケーションを選択します。

  ![](configure-images/2.2-add-application.png "モバイル アプリケーションからアクセスする必要があるアプリケーションを選択します。")

3. アプリケーションを選択するで新しく追加したアプリケーションをもう一度選択**他のアプリケーションに対するアクセス許可**セクションし、適切な権限を付与します。

  ![](configure-images/2.3-permissions.png "アプリケーションを選択すると、もう一度その他のアプリケーション セクションへのアクセス許可で新しく追加したアプリケーションを選択し、適切な権限を与える")

4. 最後に、**保存**構成します。 これらのサービスは、モバイル アプリケーションで使用できるようになりました!



## <a name="related-links"></a>関連リンク

- [Microsoft NativeClient サンプル](https://github.com/AzureADSamples/NativeClient-MultiTarget-DotNet)
