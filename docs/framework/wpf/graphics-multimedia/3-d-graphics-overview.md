---
title: 3D 圖形概觀
description: 熟悉 Windows Presentation Foundation (WPF) 中的3D 圖形，在標記和程式程式碼中繪製、轉換和製作3D 圖形的動畫。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: aa4f45ac426c59b829b6be9e63e8f0ed50512661
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358917"
---
# <a name="3d-graphics-overview"></a>3D 圖形概觀
<a name="introduction"></a> 中的3D 功能 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 可讓開發人員在標記和程式程式碼中繪製、轉換和製作3d 圖形的動畫。 開發人員可以結合2D 和3D 圖形來建立豐富的控制項、提供複雜的資料圖解，或強化應用程式介面的使用者體驗。 中的3D 支援 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 並非設計來提供全功能的遊戲開發平臺。 本主題提供圖形系統中3D 功能的總覽 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2D 容器中的3D  
 中的3D 圖形內容 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 封裝在 <xref:System.Windows.Controls.Viewport3D> 可參與二維元素結構的元素中。 圖形系統會將視為 <xref:System.Windows.Controls.Viewport3D> 二維視覺元素，就像許多其他的一樣 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 <xref:System.Windows.Controls.Viewport3D> 以視窗（視口）形式的形式提供給三維場景。 更精確地說，它是投射3D 場景的介面。  
  
 在傳統2D 應用程式中，請使用 <xref:System.Windows.Controls.Viewport3D> 與另一個容器元素（如格線或畫布）相同的方式。  雖然您可以 <xref:System.Windows.Controls.Viewport3D> 在相同的場景圖形中使用與其他2d 繪圖物件，但是無法在中貫穿2d 和3d 物件 <xref:System.Windows.Controls.Viewport3D> 。  本主題將著重于如何在中繪製3D 圖形 <xref:System.Windows.Controls.Viewport3D> 。  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3D 座標空間  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]2d 圖形的座標系統會找出呈現區域左上角的原點 (通常是畫面) 。 在2D 系統中，正 X 軸的值會往右往右，y 軸的正值則會往下進行。  不過，在3D 座標系統中，原點是位於轉譯區域的中央，而正 X 軸的值會往右，但 y 軸的正值是往右，但正 Z 軸的值會從原點朝檢視器往外繼續。  
  
 ![座標系統](./media/coordsystem-1.png "CoordSystem-1")  
傳統2D 和3D 座標系統標記法  
  
 這些軸所定義的空間是中3D 物件參考的靜止框架 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 當您在此空間中建置模型，並建立光線和觀景窗來檢視這些模型時，有助於區分此靜態參考座標系 (或稱為「世界空間」) 與您為每個模型套用轉換時建立的當地參考座標系。 也請記住，在世界空間中的物件取決於光線和觀景窗設定，可能看起來完全不同，或者完全無法看見，但觀景窗的位置不會改變世界空間中物件的位置。  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>觀景窗和投影  
 在2D 中工作的開發人員習慣在二維螢幕上定位繪圖基本專案。 當您建立3D 場景時，請務必記得您實際上是建立3D 物件的2D 標記法。 因為3D 場景會根據旁觀者的觀點來看起來不同，所以您必須指定該點。 <xref:System.Windows.Media.Media3D.Camera>類別可讓您為3d 場景指定此點的觀點。  
  
 若要瞭解3D 場景在2D 表面上的呈現方式，另一種方式是將場景描述為投影至觀察介面。 可 <xref:System.Windows.Media.Media3D.ProjectionCamera> 讓您指定不同的預測和其屬性，以變更旁觀者看到3d 模型的方式。 <xref:System.Windows.Media.Media3D.PerspectiveCamera>指定 foreshortens 場景的投射。  換句話說，會 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 提供沒影點的觀點。  您可以指定觀景窗在場景座標空間中的位置、觀景窗的方向和視野，以及定義場景中「向上」方向的向量。 下圖說明的 <xref:System.Windows.Media.Media3D.PerspectiveCamera> 投射。  
  
 的 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 和 <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 屬性會 <xref:System.Windows.Media.Media3D.ProjectionCamera> 限制相機投影的範圍。 由於觀景窗可能會位在場景中的任何地方，觀景窗有可能實際上就位在模型內部或非常靠近模型，因此更難正確區分物件。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 可讓您指定相機的最小距離，而不會繪製物件。  相反 <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> 地，您可以指定與相機之間的距離，而不會繪製物件，如此可確保在場景中不會包含物件太遠無法辨識。  
  
 ![觀景窗設定](./media/coordsystem-6.png "CoordSystem-6")  
觀景窗位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> 指定3D 模型至2D 視覺介面的垂直投射。 與其他觀景窗相同，它會指定位置、檢視方向和「向上」方向。 但是，不同 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 于描述不包含透視透視的投射。 換句話說， <xref:System.Windows.Media.Media3D.OrthographicCamera> 它會描述其邊為平行的觀賞方塊，而不是其邊符合相機中某個點的一個。 下圖顯示使用和所查看的相同模型 <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> 。  
  
 ![正視投影和透視投影](./media/camera-projections4.png "Camera_projections4")  
透視投影和正視投影  
  
 下列程式碼示範一些典型的觀景窗設定。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>模型和網格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D> 是表示泛型3D 物件的抽象基類。 若要建立3D 場景，您需要有一些物件可供查看，而組成場景圖形的物件則衍生自 <xref:System.Windows.Media.Media3D.Model3D> 。 目前 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支援使用模型化幾何 <xref:System.Windows.Media.Media3D.GeometryModel3D> 。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>此模型的屬性會採用網格基本類型。  
  
 若要建立模型，請先建立基元 (也就是網格)。 3D 基本類型是形成單一 3D 實體的頂點集合。 大部分的3D 系統都會提供以最簡單的封閉圖為模型的基本專案：三個頂點所定義的三角形。  因為三角形的三個點共面，所以您可以持續加入三角形，以塑造出更複雜的圖形 (稱為網格)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 系統目前提供 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 類別，可讓您指定任何幾何; 它目前不支援預先定義的3d 基本專案，例如球體和立方形式。 藉 <xref:System.Windows.Media.Media3D.MeshGeometry3D> 由指定三角形頂點的清單做為其屬性，開始建立 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。 每個頂點都會指定為 <xref:System.Windows.Media.Media3D.Point3D> 。   (中的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，請將此屬性指定為三中分組的數位清單，以表示每個頂點的座標。 ) 根據其幾何的不同，您的網格可能是由許多三角形組成，其中有些三角形會 (頂點) 的部分共用相同的角落。 若要正確繪製網格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要哪些三角形共用哪些頂點的相關資訊。 您可以藉由指定具有屬性的三角形索引清單來提供此資訊 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 。 這份清單會指定清單中指定的點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 將決定三角形的順序。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在上述範例中， <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 清單會指定八個頂點來定義立方體狀網格。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>屬性會指定三個索引的12個群組清單。  清單中的每個數位都會參考清單中的位移 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。  例如，清單指定的前三個頂點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 是 (1、1、0) 、 (0、1、0) 和 (0、0、0) 。 清單所指定的前三個索引 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> 為0、2和1，對應至清單中的第一個、第三個和第二個點 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> 。 因此，組成立方體模型的第一個三角形將會從 (1,1,0) 到 (0,1,0) 到 (0,0,0) 組成，其餘的十一個三角形也同樣如此決定。  
  
 您可以藉由指定和屬性的值，繼續定義模型 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 。  若要轉譯模型的表面，圖形系統需要表面在任意指定的三角形處面對哪個方向的資訊。 系統會使用此資訊來進行模型的光線計算︰直接面向光源的表面看起來就會比偏離光線一些角度的表面還亮。 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置座標決定預設的法向向量，但是您也可以指定不同的法向向量以模擬曲面的外觀。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>屬性會指定的集合 <xref:System.Windows.Point> ，這個集合會告知圖形系統如何對應座標，以決定紋理繪製到網格頂點的方式。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 指定為介於0和1（含）之間的值。  如同 <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> 屬性，圖形系統可以計算預設材質座標，但您可以選擇設定不同的材質座標，以控制包含部分重複模式的材質對應。 您可以在後續的主題或 Managed Direct3D SDK 中找到有關紋理座標的詳細資訊。  
  
 下列範例示範如何以程序性程式碼建立立方體模型的一個面。 您可以將整個 cube 繪製為單一 GeometryModel3D;此範例會將 cube 的臉部繪製為不同的模型，以便稍後將不同的材質套用至每個臉部。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>對模型套用材質  
  
 若要讓網格看起來像三維物件，就必須套用紋理以涵蓋由其頂點和三角形所定義的表面，讓觀景窗可以點亮並投影表面。 在2D 中，您可以使用 <xref:System.Windows.Media.Brush> 類別，將色彩、模式、漸層或其他視覺內容套用至螢幕的區域。  不過，3D 物件的外觀是光源模型的函式，而不只是套用的色彩或模式。 真實的物體會根據物體表面的質地以不同方式反射光線︰光滑而閃亮的表面看起來會與粗糙或黯淡的表面不同，而一些物體看起來會吸收光線，一些物體則會發亮。 您可以將所有相同的筆刷套用至您可以套用至2D 物件的3D 物件，但是您無法直接套用它們。  
  
 若要定義模型介面的特性，請 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用 <xref:System.Windows.Media.Media3D.Material> 抽象類別。 Material 的具體子類別會決定模型表面的一些外觀特性，每個特性也提供您可以傳遞 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 屬性。  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial> 指定將筆刷套用至模型，就好像該模型已擴散。 使用 DiffuseMaterial 最類似在2D 模型上直接使用筆刷;模型介面不會以亮燈的方式反映。  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial> 指定要將筆刷套用至模型，就好像模型的表面很難或發亮，能夠反映醒目顯示。 您可以藉由指定屬性的值，來設定材質將建議此反射品質的程度，或「眼」 <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> 。  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial> 可讓您指定要套用紋理，就好像模型發出的燈光等於筆刷的色彩一樣。 這不會讓模型變成光源。不過，這會影響陰影處理的方式，與透過 DiffuseMaterial 或 SpecularMaterial 加上紋理的方式不同。  
  
 為了獲得更好的效能， (的 backfaces， <xref:System.Windows.Media.Media3D.GeometryModel3D> 因為它們位於相機的模型相對側，) 從場景中挑選。  若要指定 <xref:System.Windows.Media.Media3D.Material> 要套用至模型（例如平面）背面的，請設定模型的 <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> 屬性。  
  
 若要達到某些表面質地，例如發光或反射效果，您可以對模型連續套用數種不同的筆刷。 您可以使用類別來套用和重複使用多個材質 <xref:System.Windows.Media.Media3D.MaterialGroup> 。 在多個轉譯階段中，會從頭到尾套用 MaterialGroup 的子系。  
  
 下列程式碼範例示範如何將純色和繪圖作為筆刷套用至3D 模型。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
 [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]  
 [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>場景照明  
 3D 圖形中的燈光可在真實世界中執行燈光：讓表面變成可見。 而且，光線還會決定投影時要包含場景的哪個部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光線物件會建立各種光線和陰影效果，而且會仿照真實世界各種光線的行為。 在場景中包含至少一個光線，否則不會顯示任何模型。  
  
 下列燈光衍生自基類 <xref:System.Windows.Media.Media3D.Light> ：  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>：提供的環境光源會一致地照亮所有物件，無論其位置或方向為何。  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>：類似于遠處光源。  方向光源具有 <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> 指定為 Vector3D，但沒有指定的位置。  
  
- <xref:System.Windows.Media.Media3D.PointLight>：類似附近的光源。 PointLights 有一個位置，並從該位置投射光線。 場景中的物件會根據其相對於光線的位置和距離來照明。 <xref:System.Windows.Media.Media3D.PointLightBase> 公開 <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> 屬性，此屬性會決定要讓模型不會被光線照亮的距離。 PointLight 也會公開衰減屬性，以決定光線強度如何隨著距離而降低。 您可以為光線衰減指定常數、線性插補或二次插補。  
  
- <xref:System.Windows.Media.Media3D.SpotLight>：繼承自 <xref:System.Windows.Media.Media3D.PointLight> 。 Spotlight 照明的方式類似 PointLight，而且有位置和方向兩者。 它們投射在錐形區域中 <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> ，並以 <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> 度數指定的屬性（以度為單位）。  
  
 燈光是 <xref:System.Windows.Media.Media3D.Model3D> 物件，因此您可以轉換和建立燈光屬性的動畫，包括位置、色彩、方向和範圍。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>轉換模型  
 當您建立模型時，模型在場景中有特定的位置。 若要在場景中四處移動模型、旋轉模型，或變更模型的大小，變更定義模型的頂點本身並不實用。  相反地，您可以將轉換套用至模型，就像在2D 中一樣。  
  
 每個模型物件都有一個屬性，可 <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> 讓您移動、調整大小或調整模型的大小。  當您套用轉換時，可以透過轉換所指定的任何向量或值，有效率地位移模型的所有點。 換句話說，您已經轉換定義模型所在的座標空間 (「模型空間」)，但尚未變更在整個場景的座標系統 (「世界空間」) 中組成模型幾何的值。  
  
 如需轉換模型的詳細資訊，請參閱 [3D 轉換總覽](3-d-transformations-overview.md)。  
  
<a name="animations"></a>
## <a name="animating-models"></a>以動畫顯示模型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3d 執行會參與與2d 圖形相同的計時和動畫系統。 換句話說，若要以動畫顯示3D 場景，請建立其模型的屬性動畫。 您可以直接以動畫顯示基元的屬性，但是以動畫顯示變更模型位置或外觀的轉換通常更容易。 因為轉換可以套用至 <xref:System.Windows.Media.Media3D.Model3DGroup> 物件和個別模型，所以您可以將一組動畫套用至 system.windows.media.media3d.model3dgroup> 的子系，並將另一組動畫套用到子物件的群組。 您也可以以動畫顯示場景光線的屬性，達到各種視覺效果。 最後，您還可以選擇以動畫顯示觀景窗的位置或視野，以動畫顯示投影本身。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 計時和動畫系統的背景資訊，請參閱[動畫概觀](animation-overview.md)、[分鏡腳本概觀](storyboards-overview.md)，以及 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)等主題。  
  
 若要以動畫顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的物件，您要建立時間軸、定義動畫 (這實際上是某些屬性值隨時間的變化)，並指定要套用動畫的屬性。 因為3D 場景中的所有物件都是的子系 <xref:System.Windows.Controls.Viewport3D> ，所以您想要套用至場景之任何動畫的目標屬性都是 Viewport3D 的屬性。  
  
 假設您想要讓模型就地搖晃。 您可以選擇將套用 <xref:System.Windows.Media.Media3D.RotateTransform3D> 至模型，並將其旋轉軸的動畫從一個向量繪製到另一個向量。 下列程式碼範例示範如何對轉換之 Rotation3D 的 Axis 屬性套用 Vector3DAnimation，假設 RotateTransform3D 是要使用 TransformGroup 對模型套用的其中一個轉換。  
  
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
 若要轉譯場景，請將模型和燈光加入至 <xref:System.Windows.Media.Media3D.Model3DGroup> ，然後將設定 <xref:System.Windows.Media.Media3D.Model3DGroup> 為的 <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> <xref:System.Windows.Media.Media3D.ModelVisual3D> 。 將加入 <xref:System.Windows.Media.Media3D.ModelVisual3D> 至的 <xref:System.Windows.Controls.Viewport3D.Children%2A> 集合 <xref:System.Windows.Controls.Viewport3D> 。 藉 <xref:System.Windows.Controls.Viewport3D> 由設定其屬性，將攝影機新增至 <xref:System.Windows.Controls.Viewport3D.Camera%2A> 。  
  
 最後，將加入 <xref:System.Windows.Controls.Viewport3D> 至視窗。 當 <xref:System.Windows.Controls.Viewport3D> 包含做為版面設定項目（如 Canvas）的內容時，請設定 Viewport3D 的大小，方法是將其 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 屬性設定 (繼承自 <xref:System.Windows.FrameworkElement>) 。  
  
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
