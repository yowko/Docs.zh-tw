---
title: 3D 圖形概觀
description: 熟悉 Windows Presentation Foundation （WPF）中的3D 圖形，在標記和程式性程式碼中繪製、轉換和建立3D 圖形的動畫。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 51da6a1ed6d5e98b99c64ee23be52f7b2385897f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853877"
---
# <a name="3d-graphics-overview"></a>3D 圖形概觀
<a name="introduction"></a>中的3D 功能 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可讓開發人員在標記和程式性程式碼中繪製、轉換和建立3d 圖形的動畫。 開發人員可以結合2D 和3D 圖形來建立豐富的控制項、提供資料的複雜圖解，或增強應用程式介面的使用者體驗。 中的3D 支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 並非設計來提供全功能的遊戲開發平臺。 本主題提供圖形系統中3D 功能的總覽 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2D 容器中的3D  
 中的3D 圖形內容 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝在 <xref:System.Windows.Controls.Viewport3D> 可參與二維元素結構的元素中。 圖形系統會將視為 <xref:System.Windows.Controls.Viewport3D> 二維視覺元素，如同中的許多其他專案 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 <xref:System.Windows.Controls.Viewport3D>以視窗（一個區）的形式呈現在三維場景中。 更精確的說，它是投射3D 場景的介面。  
  
 在傳統2D 應用程式中，請使用， <xref:System.Windows.Controls.Viewport3D> 如同格線或畫布之類的另一個容器元素。  雖然您可以 <xref:System.Windows.Controls.Viewport3D> 在相同的場景圖形中使用與其他2d 繪圖物件，但是無法在中貫穿2d 和3d 物件 <xref:System.Windows.Controls.Viewport3D> 。  本主題將著重于如何在內繪製3D 圖形 <xref:System.Windows.Controls.Viewport3D> 。  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3D 座標空間  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]2d 圖形的座標系統會在轉譯區域（通常是螢幕）的左上方尋找原點。 在2D 系統中，正 X 軸值會繼續向右，而 y 軸的正值則是往下進行。  不過，在3D 座標系統中，原點位於轉譯區域的中央，而正 X 軸的值會繼續往右，但 y 軸的正值是往上移，而正 Z 軸值則是從原點向外移到檢視器。  
  
 ![座標系統](./media/coordsystem-1.png "CoordSystem-1")  
傳統2D 和3D 座標系統標記法  
  
 這些軸所定義的空間是中，3D 物件的靜止參考框架 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 當您在此空間中建置模型，並建立光線和觀景窗來檢視這些模型時，有助於區分此靜態參考座標系 (或稱為「世界空間」) 與您為每個模型套用轉換時建立的當地參考座標系。 也請記住，在世界空間中的物件取決於光線和觀景窗設定，可能看起來完全不同，或者完全無法看見，但觀景窗的位置不會改變世界空間中物件的位置。  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>觀景窗和投影  
 在2D 中工作的開發人員習慣在二維畫面上放置繪圖基本專案。 當您建立3D 場景時，請務必記住，您實際上是建立3D 物件的2D 標記法。 因為3D 場景看起來會根據旁觀者的觀點而有所不同，所以您必須指定該點的觀點。 <xref:System.Windows.Media.Media3D.Camera>類別可讓您指定3d 場景的這個觀點。  
  
 另一種瞭解3D 場景如何在2D 表面上呈現的方式，是將場景描述為投影到觀賞介面上。 可 <xref:System.Windows.Media.Media3D.ProjectionCamera> 讓您指定不同的投影和其屬性，以變更旁觀者看到3d 模型的方式。 <xref:System.Windows.Media.Media3D.PerspectiveCamera>會指定 foreshortens 場景的投影。  換句話說，會 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 提供消失點的觀點。  您可以指定觀景窗在場景座標空間中的位置、觀景窗的方向和視野，以及定義場景中「向上」方向的向量。 下圖說明的 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 投影。  
  
 的 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 和 <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 屬性會 <xref:System.Windows.Media.Media3D.ProjectionCamera> 限制相機投射的範圍。 由於觀景窗可能會位在場景中的任何地方，觀景窗有可能實際上就位在模型內部或非常靠近模型，因此更難正確區分物件。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>可讓您指定相機的最小距離，而不會繪製物件。  相反地，可 <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 讓您指定與相機相距的距離，但不會繪製物件，這可確保不會在場景中包含物件太遠而無法辨識。  
  
 ![觀景窗設定](./media/coordsystem-6.png "CoordSystem-6")  
觀景窗位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>指定3D 模型到2D 視覺效果介面的正向投射。 與其他觀景窗相同，它會指定位置、檢視方向和「向上」方向。 不過，與不同的 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 是，它會描述不包含透視透視的投影。 換句話說， <xref:System.Windows.Media.Media3D.OrthographicCamera> 描述一個邊緣為平行的觀看方塊，而不是其一邊符合相機中某個點的一個。 下圖顯示使用和來查看的相同模型 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 。  
  
 ![正視投影和透視投影](./media/camera-projections4.png "Camera_projections4")  
透視投影和正視投影  
  
 下列程式碼示範一些典型的觀景窗設定。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>模型和網格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D>是表示泛型3D 物件的抽象基類。 若要建立3D 場景，您需要有一些物件可供您查看，而組成場景圖形的物件則衍生自 <xref:System.Windows.Media.Media3D.Model3D> 。 目前 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援使用模型化幾何 <xref:System.Windows.Media.Media3D.GeometryModel3D> 。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>此模型的屬性會採用網格基本類型。  
  
 若要建立模型，請先建立基元 (也就是網格)。 3D 基本類型是形成單一 3D 實體的頂點集合。 大部分的3D 系統都會提供以最簡單的封閉圖為模型的基本專案：由三個頂點定義的三角形。  因為三角形的三個點共面，所以您可以持續加入三角形，以塑造出更複雜的圖形 (稱為網格)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 系統目前提供 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 類別，可讓您指定任何幾何，但目前不支援預先定義的3d 基本型別，例如球體和三型表單。 藉 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 由將三角形頂點清單指定為其屬性，開始建立 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。 每個頂點都指定為 <xref:System.Windows.Media.Media3D.Point3D> 。  （在中 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，將此屬性指定為三中分組的數位清單，代表每個頂點的座標）。根據其幾何而定，您的網格可能是由許多三角形組成，其中有些會共用相同的角落（頂點）。 若要正確繪製網格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要哪些三角形共用哪些頂點的相關資訊。 您可以藉由指定包含屬性的三角形索引清單來提供這項資訊 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 。 此清單會指定清單中指定的點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 將決定三角形的順序。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在上述範例中， <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 清單會指定八個頂點來定義立方體形狀的網格。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>屬性會指定三個索引的十二個群組清單。  清單中的每個數位都是指清單中的位移 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。  例如，清單所指定的前三個頂點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 為（1，1，0）、（0，1，0）和（0，0，0）。 清單所指定的前三個索引 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 為0、2和1，對應至清單中的第一個、第三和第二個點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。 因此，組成立方體模型的第一個三角形將會從 (1,1,0) 到 (0,1,0) 到 (0,0,0) 組成，其餘的十一個三角形也同樣如此決定。  
  
 您可以藉由指定和屬性的值，繼續定義模型 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 。  若要轉譯模型的表面，圖形系統需要表面在任意指定的三角形處面對哪個方向的資訊。 系統會使用此資訊來進行模型的光線計算︰直接面向光源的表面看起來就會比偏離光線一些角度的表面還亮。 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置座標決定預設的法向向量，但是您也可以指定不同的法向向量以模擬曲面的外觀。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>屬性會指定的集合 <xref:System.Windows.Point> ，告訴圖形系統如何對應座標來決定如何繪製紋理到網格的頂點。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>指定為介於0到1（含）之間的值。  就像 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> 屬性一樣，圖形系統可以計算預設材質座標，但是您可以選擇設定不同的材質座標，以控制包含重複模式部分之材質的對應，例如。 您可以在後續的主題或 Managed Direct3D SDK 中找到有關紋理座標的詳細資訊。  
  
 下列範例示範如何以程序性程式碼建立立方體模型的一個面。 您可以將整個 cube 繪製成單一 GeometryModel3D;這個範例會將 cube 的臉部繪製為不同的模型，以便稍後將個別材質套用至每個臉部。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>對模型套用材質  
  
 若要讓網格看起來像三維物件，就必須套用紋理以涵蓋由其頂點和三角形所定義的表面，讓觀景窗可以點亮並投影表面。 在2D 中，您可以使用 <xref:System.Windows.Media.Brush> 類別，將色彩、模式、漸層或其他視覺內容套用至螢幕的區域。  不過，3D 物件的外觀是光源模型的函式，而不只是套用至其色彩或模式的功能。 真實的物體會根據物體表面的質地以不同方式反射光線︰光滑而閃亮的表面看起來會與粗糙或黯淡的表面不同，而一些物體看起來會吸收光線，一些物體則會發亮。 您可以將所有相同的筆刷套用至可以套用至2D 物件的3D 物件，但無法直接套用。  
  
 若要定義模型介面的特性，會 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 <xref:System.Windows.Media.Media3D.Material> 抽象類別。 Material 的具體子類別會決定模型表面的一些外觀特性，每個特性也提供您可以傳遞 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 屬性。  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>指定筆刷會套用至模型，就好像該模型的擴散點一樣。 使用 DiffuseMaterial 與直接在2D 模型上使用筆刷相似，模型表面不會反映光線，如同發亮。  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>指定筆刷會套用至模型，就像模型的表面很難或發亮，可以反映重點。 您可以藉由指定屬性的值，設定材質會建議此反射品質的程度，或「照射」 <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> 。  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>可讓您指定將套用材質，如同模型發出的光線等於筆刷的色彩。 這不會讓模型變成光源。不過，這會影響陰影處理的方式，與透過 DiffuseMaterial 或 SpecularMaterial 加上紋理的方式不同。  
  
 為獲得較佳的效能，的 backfaces <xref:System.Windows.Media.Media3D.GeometryModel3D> （那些表面因為與相機中的型號相反而無法觀看）會從場景中挑選。  若要指定 <xref:System.Windows.Media.Media3D.Material> 要套用至模型（例如平面）背面的，請設定模型的 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> 屬性。  
  
 若要達到某些表面質地，例如發光或反射效果，您可以對模型連續套用數種不同的筆刷。 您可以使用類別來套用及重複使用多個材質 <xref:System.Windows.Media.Media3D.MaterialGroup> 。 在多個轉譯階段中，會從頭到尾套用 MaterialGroup 的子系。  
  
 下列程式碼範例示範如何將純色和繪圖當做筆刷套用至3D 模型。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>場景照明  
 3D 圖形中的燈會執行真實世界中的燈：使表面可見。 而且，光線還會決定投影時要包含場景的哪個部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光線物件會建立各種光線和陰影效果，而且會仿照真實世界各種光線的行為。 在場景中至少包含一個光源，否則將看不到任何模型。  
  
 下列光源衍生自基類 <xref:System.Windows.Media.Media3D.Light> ：  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>：提供環境光源，不論其位置或方向為何，都會一致地照亮所有物件。  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>：類似于較遠的光源。  方向光源具有 <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> 指定的做為 Vector3D，但沒有指定的位置。  
  
- <xref:System.Windows.Media.Media3D.PointLight>：類似于附近光源。 PointLights 有一個位置，並從該位置投射光線。 場景中的物件會根據其相對於光線的位置和距離來照明。 <xref:System.Windows.Media.Media3D.PointLightBase>公開 <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> 屬性，它會決定光線不會照亮模型的距離。 PointLight 也會公開衰減屬性，以決定光線強度如何隨著距離而降低。 您可以為光線衰減指定常數、線性插補或二次插補。  
  
- <xref:System.Windows.Media.Media3D.SpotLight>：繼承自 <xref:System.Windows.Media.Media3D.PointLight> 。 Spotlight 照明的方式類似 PointLight，而且有位置和方向兩者。 它們會以 <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> 度為單位，由和屬性所設定的圓錐形區域中的專案光線 <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> 。  
  
 光源是 <xref:System.Windows.Media.Media3D.Model3D> 物件，因此您可以轉換並建立淺屬性的動畫，包括位置、色彩、方向和範圍。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>轉換模型  
 當您建立模型時，模型在場景中有特定的位置。 若要在場景中四處移動模型、旋轉模型，或變更模型的大小，變更定義模型的頂點本身並不實用。  相反地，如同在2D 中，您會將轉換套用至模型。  
  
 每個模型物件都有一個屬性，可 <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> 讓您移動、調整大小或調整模型的大小。  當您套用轉換時，可以透過轉換所指定的任何向量或值，有效率地位移模型的所有點。 換句話說，您已經轉換定義模型所在的座標空間 (「模型空間」)，但尚未變更在整個場景的座標系統 (「世界空間」) 中組成模型幾何的值。  
  
 如需轉換模型的詳細資訊，請參閱[3D 轉換總覽](3-d-transformations-overview.md)。  
  
<a name="animations"></a>
## <a name="animating-models"></a>以動畫顯示模型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 實作為與2d 圖形相同的計時和動畫系統。 換句話說，若要以動畫顯示3D 場景，請以動畫顯示其模型的屬性。 您可以直接以動畫顯示基元的屬性，但是以動畫顯示變更模型位置或外觀的轉換通常更容易。 因為轉換可以套用至 <xref:System.Windows.Media.Media3D.Model3DGroup> 物件以及個別模型，所以可以將一組動畫套用至 system.windows.media.media3d.model3dgroup> 的子系，並將另一組動畫套用至子物件的群組。 您也可以以動畫顯示場景光線的屬性，達到各種視覺效果。 最後，您還可以選擇以動畫顯示觀景窗的位置或視野，以動畫顯示投影本身。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 計時和動畫系統的背景資訊，請參閱[動畫概觀](animation-overview.md)、[分鏡腳本概觀](storyboards-overview.md)，以及 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)等主題。  
  
 若要以動畫顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的物件，您要建立時間軸、定義動畫 (這實際上是某些屬性值隨時間的變化)，並指定要套用動畫的屬性。 因為3D 場景中的所有物件都是的子系 <xref:System.Windows.Controls.Viewport3D> ，所以您想要套用至場景之任何動畫的目標屬性都是 Viewport3D 的屬性。  
  
 假設您想要讓模型就地搖晃。 您可以選擇將套用 <xref:System.Windows.Media.Media3D.RotateTransform3D> 至模型，並將其旋轉的軸以動畫顯示到另一個向量。 下列程式碼範例示範如何對轉換之 Rotation3D 的 Axis 屬性套用 Vector3DAnimation，假設 RotateTransform3D 是要使用 TransformGroup 對模型套用的其中一個轉換。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>將3D 內容新增至視窗  
 若要轉譯場景，請將模型和光源加入至 <xref:System.Windows.Media.Media3D.Model3DGroup> ，然後將設定 <xref:System.Windows.Media.Media3D.Model3DGroup> 為 <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> 的 <xref:System.Windows.Media.Media3D.ModelVisual3D> 。 將加入 <xref:System.Windows.Media.Media3D.ModelVisual3D> 至的 <xref:System.Windows.Controls.Viewport3D.Children%2A> 集合 <xref:System.Windows.Controls.Viewport3D> 。 藉 <xref:System.Windows.Controls.Viewport3D> 由設定其屬性，將相機新增至 <xref:System.Windows.Controls.Viewport3D.Camera%2A> 。  
  
 最後，將加入 <xref:System.Windows.Controls.Viewport3D> 至視窗。 當當做 <xref:System.Windows.Controls.Viewport3D> 版面設定項目（例如 Canvas）的內容包含時，請設定其 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性（繼承自）來指定 Viewport3D 的大小 <xref:System.Windows.FrameworkElement> 。  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [3D 轉換概觀](3-d-transformations-overview.md)
- [最大化 WPF 3D 效能](maximize-wpf-3d-performance.md)
- [操作說明主題](3-d-graphics-how-to-topics.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
