---
title: SceneKit
ms.topic: article
ms.prod: xamarin
ms.assetid: 19049ED5-B68E-4A0E-9D57-B7FAE3BB8987
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 06/14/2017
ms.openlocfilehash: 785faab84c4f3c5176750f4d86eeaeae3bb9332d
ms.sourcegitcommit: 6cd40d190abe38edd50fc74331be15324a845a28
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="scenekit"></a>SceneKit

シーン キットは 3D シーン グラフを 3D 画像の操作を簡略化する API です。 OS X 10.8 で初めて導入されましたし、iOS 8 に来たようになりました。 シーン キット イマーシブ 3D 視覚エフェクトとカジュアル 3D ゲームを作成する必要はありません OpenGL の専門知識。 シーン graph の一般的な概念を構築、シーン キットを抽象 OpenGL と非常に簡単に行う追加 3D コンテンツをアプリケーションに OpenGL ES の複雑な作業です。 ただし、OpenGL エキスパートの場合は、シーン キットによっても OpenGL と直接に結び付けることのサポートがあります。 また、物理学など、3 D グラフィックスを補足する多数の機能が含まれていて、いくつか他の Apple などのフレームワーク、コア アニメーション、Core のイメージおよびスプライト キット予算との統合します。

シーン キットは、非常に作業を容易にします。 宣言型の API はレンダリングの対処をすることをお勧めします。 単に、シーンの設定、プロパティを追加し、シーン キット ハンドル、シーンのレンダリングします。

使用してシーン グラフを作成するシーン キットを使用する、`SCNScene`クラスです。 シーンにはインスタンスで表されたノードの階層が含まれています`SCNNode`、3 D 空間内の場所を定義します。 各ノードは、次の図に示すように、geometry、照明の外観に影響する材料などのプロパティを持ちます。

![](scenekit-images/image7.png "SceneKit 階層") 

## <a name="create-a-scene"></a>シーンを作成します。

画面に表示シーンをするためには、追加する、`SCNView`ビューのシーン プロパティに割り当てるとします。 さらに、シーンを変更する場合は、`SCNView`表示、変更を自動的に更新されます。

```csharp
scene = SCNScene.Create ();
sceneView = new SCNView (View.Frame);
sceneView.Scene = scene;
```

モデリング ツールで 3d を使用してエクスポートされたファイルとプログラムでジオメトリ プリミティブから、シーンを設定できます。 たとえば、球面を作成し、シーンに追加する方法を示します。

```csharp
sphere = SCNSphere.Create (10.0f);
sphereNode = SCNNode.FromGeometry (sphere);
sphereNode.Position = new SCNVector3 (0, 0, 0);
scene.RootNode.AddChildNode (sphereNode);
```

## <a name="adding-light"></a>光を追加します。

この時点で、球何も表示されません、シーン内のライトがないためです。 アタッチ`SCNLight`インスタンス ノードをライトをシーン キットを作成します。 周囲の照明方向光源のさまざまなフォームからまでライトのいくつかの種類があります。 たとえば、次のコードでは、球片側全方向のライトが作成されます。

```csharp
// omnidirectional light
var light = SCNLight.Create ();
var lightNode = SCNNode.Create ();
light.LightType = SCNLightType.Omni;
light.Color = UIColor.Blue;
lightNode.Light = light;
lightNode.Position = new SCNVector3 (-40, 40, 60);
scene.RootNode.AddChildNode (lightNode);
```

全方向照明には、その結果、偶数の照明のソート懐中電灯を当てたのように拡散リフレクションが生成されます。 ない方向が威力を発揮均等にすべての方向とは、環境光を作成すると同様に、です。 気分照明:) のように考えると

```csharp
// ambient light
ambientLight = SCNLight.Create ();
ambientLightNode = SCNNode.Create ();
ambientLight.LightType = SCNLightType.Ambient;
ambientLight.Color = UIColor.Purple;
ambientLightNode.Light = ambientLight;
scene.RootNode.AddChildNode (ambientLightNode);
```

インプレース ライトでの球がシーンで表示されます。

![](scenekit-images/image8.png "球が点灯している場合は、シーン内に表示されます。")
 
## <a name="adding-a-camera"></a>カメラの追加

カメラ (SCNCamera) をシーンに追加の観点を変更します。 カメラを追加するパターンと似ています。 カメラを作成、ノードにアタッチし、シーン ノードを追加します。

```csharp
// camera
camera = new SCNCamera {
    XFov = 80,
    YFov = 80
};
cameraNode = new SCNNode {
    Camera = camera,
    Position = new SCNVector3 (0, 0, 40)
};
scene.RootNode.AddChildNode (cameraNode);
```

コード上、コンス トラクターを使用してオブジェクトを作成するシーン キットまたは作成するファクトリ メソッドからことがわかります。 前者は、c# の初期化子構文を使用してがどれを使用してほぼ好みの問題です。

インプレース カメラでは、球体全体は、ユーザーに表示されます。

![](scenekit-images/image9.png "球体全体がユーザーに表示されます。")
 
シーンを同様に、追加のライトを追加できます。 どのように、いくつかの詳細全方向光を次に示します。

![](scenekit-images/image10.png "いくつかの詳細全方向点灯球")
 
設定することによってさらに、`sceneView.AllowsCameraControl = true`ユーザーの観点タッチ ジェスチャには変更できます。

### <a name="materials"></a>素材

SCNMaterial クラスを使用したマテリアルが作成されます。 球のサーフェイスにイメージを追加する例では、イメージに設定素材の*ディフューズ*内容。

```csharp
material = SCNMaterial.Create ();
material.Diffuse.Contents = UIImage.FromFile ("monkey.png");
sphere.Materials = new SCNMaterial[] { material };
```

これは、層の次のように、イメージをノードに。

![](scenekit-images/image11.png "球体にイメージをレイヤー化")
 
他の種類の照明すぎるに応答するマテリアルを設定できます。 たとえば、オブジェクトにできる光沢のあるその反射の効果の内容を設定している画面では、明るい部分を次に示すようにその結果、反射の効果の反射を表示します。

![](scenekit-images/image12.png "光沢のある結果として、画面上の明るい部分反射の効果のリフレクションを使用して行われたオブジェクト")
 
マテリアルは非常に柔軟な非常にわずかなコードでは多くを実現することができます。 たとえば、設定ではなく、拡散の内容をイメージに設定反射の内容代わりにします。

```csharp
material.Reflective.Contents = UIImage.FromFile ("monkey.png");
```

観点の独立した、球体内で視覚的に留まるように、サルが表示されます。

### <a name="animation"></a>アニメーション

シーン キットは、アニメーションで適切に動作設計されています。 暗黙的または明示的なの両方のアニメーションを作成して、コア アニメーション レイヤー ツリーからシーンのレンダリングもできます。 シーン Kit は、独自の transition クラスを提供する暗黙的なアニメーションを作成するときに`SCNTransaction`です。

球に回転する例を次に示します。

```csharp
SCNTransaction.Begin ();
SCNTransaction.AnimationDuration = 2.0;
sphereNode.Rotation = new SCNVector4 (0, 1, 0, (float)Math.PI * 4);
SCNTransaction.Commit ();
```

アニメーション化できます回転よりはるかに多くもします。 シーン キットの多数のプロパティは、アニメーション化します。 たとえば、次のコードが素材をアニメーション化`Shininess`反射の効果のリフレクションを向上させる。

```csharp
SCNTransaction.Begin ();
SCNTransaction.AnimationDuration = 2.0;
material.Shininess = 0.1f;
SCNTransaction.Commit ();
```

シーン キットは、非常に簡単に使用します。 さまざまな制約、物理学、宣言動作、3 D のテキスト、フィールドのサポート、スプライト キット統合と少しだけ名前を Core のイメージの統合の深さなどその他の機能を提供します。