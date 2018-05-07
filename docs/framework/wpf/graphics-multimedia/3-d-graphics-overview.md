---
title: 立體圖形概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D graphics [WPF]
- graphics [WPF], 3-D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 6d44f27ccd82d535436be03092c3864e3155d1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="3-d-graphics-overview"></a>立體圖形概觀
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 功能可讓開發人員以標記和程序性程式碼繪製、轉換 3D 圖形，以及以動畫顯示 3D 圖形。 開發人員可以結合 [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] 和 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 圖形來建立豐富的控制項、提供複雜的資料說明，或者加強應用程式介面的使用者體驗。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 支援不適用於提供完整功能的遊戲開發平台。 本主題將提供 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形系統中 [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] 功能的概觀。  
 
  
<a name="threed_in_2d"></a>   
## <a name="3-d-in-a-2-d-container"></a>2D 容器中的 3D  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 圖形中的內容[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]封裝在新項目， <xref:System.Windows.Controls.Viewport3D>，可以參與二維的元素結構。 圖形系統會將<xref:System.Windows.Controls.Viewport3D>二維的視覺項目，例如許多其他的為[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。 <xref:System.Windows.Controls.Viewport3D> 為視窗函式 — 檢視區 — 成 3d 場景。 更精確來說，是一種 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 場景投射到的表面。  
  
 在傳統[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]應用程式中，使用<xref:System.Windows.Controls.Viewport3D>如同像方格或畫布的另一個容器項目。  雖然您可以使用<xref:System.Windows.Controls.Viewport3D>與其他[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]繪圖物件相同的場景圖形中，您無法 interpenetrate[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]和[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]物件內<xref:System.Windows.Controls.Viewport3D>。  本主題將著重在如何繪製[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]圖形內<xref:System.Windows.Controls.Viewport3D>。  
  
<a name="coord_space"></a>   
## <a name="3-d-coordinate-space"></a>3D 座標空間  
 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 座標系統將原點置於轉譯區域 (通常是螢幕) 的左上角。 在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 系統中，x 軸的正值是往右，y 軸的正值則是往下。  不過在 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 座標系統中，原點是位於轉譯區域的中心，x 軸的正值是往右，但 y 軸的正值是往上，而 z 軸的正值是從原點朝向檢視器往外。  
  
 ![座標系統](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-1.png "CoordSystem 1")  
傳統的 2D 和 3D 座標系統表示法  
  
 這些軸所定義的空間是針對 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 物件的靜態參考座標系。 當您在此空間中建置模型，並建立光線和觀景窗來檢視這些模型時，有助於區分此靜態參考座標系 (或稱為「世界空間」) 與您為每個模型套用轉換時建立的當地參考座標系。 也請記住，在世界空間中的物件取決於光線和觀景窗設定，可能看起來完全不同，或者完全無法看見，但觀景窗的位置不會改變世界空間中物件的位置。  
  
<a name="cameras"></a>   
## <a name="cameras-and-projections"></a>觀景窗和投影  
 在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 環境中工作的開發人員習慣在二維的螢幕上放置繪圖基元。 當您建立 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 場景時，請務必記住，您是真的要建立 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 物件的 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 表示法。 因為 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 場景會因為旁觀者的視角而有所不同，所以您必須指定該視角。 <xref:System.Windows.Media.Media3D.Camera>類別可讓您指定為此觀點來看[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]場景。  
  
 另一種了解如何在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 表面上表示 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 場景的方式是將場景描述為在檢視表面上的投影。 <xref:System.Windows.Media.Media3D.ProjectionCamera>可讓您指定不同的投影和其屬性，以變更視景的會看到[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]模型。 A<xref:System.Windows.Media.Media3D.PerspectiveCamera>指定 foreshortens 場景的投影。  換句話說，<xref:System.Windows.Media.Media3D.PerspectiveCamera>提供梅格點觀點。  您可以指定觀景窗在場景座標空間中的位置、觀景窗的方向和視野，以及定義場景中「向上」方向的向量。 下圖說明<xref:System.Windows.Media.Media3D.PerspectiveCamera>的投影。  
  
 <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>和<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>屬性<xref:System.Windows.Media.Media3D.ProjectionCamera>限制相機的投影的範圍。 由於觀景窗可能會位在場景中的任何地方，觀景窗有可能實際上就位在模型內部或非常靠近模型，因此更難正確區分物件。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> 可讓您指定從相機超出該物件將不會繪製的最小距離。  相反地，<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>可讓您指定從相機之外不會繪製物件，可確保太遠可辨識的物件將不會包含在場景中的距離。  
  
 ![相機設定](../../../../docs/framework/wpf/graphics-multimedia/media/coordsystem-6.png "CoordSystem 6")  
觀景窗位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera> 指定的正交投影[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]模型到[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]視覺化介面。 與其他觀景窗相同，它會指定位置、檢視方向和「向上」方向。 不同於<xref:System.Windows.Media.Media3D.PerspectiveCamera>，不過<xref:System.Windows.Media.Media3D.OrthographicCamera>描述不包含透視圖投影。 換句話說，<xref:System.Windows.Media.Media3D.OrthographicCamera>描述其兩邊都是平行，而不是其中一個在相機上的點符合其邊緣的檢視方塊。 下圖顯示相同的模型，因為檢視使用<xref:System.Windows.Media.Media3D.PerspectiveCamera>和<xref:System.Windows.Media.Media3D.OrthographicCamera>。  
  
 ![正視圖和遠近景深投射](../../../../docs/framework/wpf/graphics-multimedia/media/camera-projections4.png "Camera_projections4")  
透視投影和正視投影  
  
 下列程式碼示範一些典型的觀景窗設定。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>   
## <a name="model-and-mesh-primitives"></a>模型和網格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D> 是抽象的基底類別，代表泛型[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]物件。 若要建置[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]場景，需要一些物件，若要檢視，以及構成場景圖形物件衍生自<xref:System.Windows.Media.Media3D.Model3D>。 目前，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援模型與幾何<xref:System.Windows.Media.Media3D.GeometryModel3D>。 <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>此模型的屬性會取得網狀結構基本。  
  
 若要建立模型，請先建立基元 (也就是網格)。 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 基元是形成單一 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 實體的頂點集合。 大部分 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 系統都提供以最簡單的封閉圖形 (由三個頂點定義的三角形) 塑造而成的基元。  因為三角形的三個點共面，所以您可以持續加入三角形，以塑造出更複雜的圖形 (稱為網格)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]系統目前提供<xref:System.Windows.Media.Media3D.MeshGeometry3D>類別，可讓您指定任何 geometry; 目前不支援預先定義[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]基本型別，如陳列和三次方的表單。 開始建立<xref:System.Windows.Media.Media3D.MeshGeometry3D>藉由指定一份三角形的頂點，做為其<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>屬性。 每個端點指定為<xref:System.Windows.Media.Media3D.Point3D>。  (在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中，將此屬性指定為以三個為一組的數字清單代表每個頂點的座標)。根據網格的幾何，網格可以由許多三角形組成，其中有些三角形會共用相同的角 (頂點)。 若要正確繪製網格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要哪些三角形共用哪些頂點的相關資訊。 指定一份三角形索引與提供這項資訊<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>屬性。 這份清單指定點中指定的順序<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單將會決定三角形。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在上述範例中，<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單可指定來定義 cube 形網狀結構的八個頂點。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>屬性會指定三個索引的 12 個群組的清單。  在清單中的每個數字是指的位移<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單。  例如，所指定的前三個頂點<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單是 (1,1,0)，(0,1,0)，和 (0,0,0)。 前三個索引所指定<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>清單是 0、 2 和 1，這會對應到第一、 第三，而且點中的第二個<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單。 因此，組成立方體模型的第一個三角形將會從 (1,1,0) 到 (0,1,0) 到 (0,0,0) 組成，其餘的十一個三角形也同樣如此決定。  
  
 您可以繼續指定的值來定義模型<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>和<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>屬性。  若要轉譯模型的表面，圖形系統需要表面在任意指定的三角形處面對哪個方向的資訊。 系統會使用此資訊來進行模型的光線計算︰直接面向光源的表面看起來就會比偏離光線一些角度的表面還亮。 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置座標決定預設的法向向量，但是您也可以指定不同的法向向量以模擬曲面的外觀。  
  
 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>屬性指定的集合<xref:System.Windows.Point>s 告知圖形系統如何對應，以決定如何紋理會繪製到網狀結構的頂點的座標。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> 已指定為介於 0 和 1 (含) 之間的值。  如同<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>屬性，圖形系統可以計算預設材質座標，但是您可以選擇設定不同的紋理座標來控制包含重複的模式，例如對紋理的對應。 您可以在後續的主題或 Managed Direct3D SDK 中找到有關紋理座標的詳細資訊。  
  
 下列範例示範如何以程序性程式碼建立立方體模型的一個面。 請注意，您可以將整個立方體繪製為單一一個 GeometryModel3D；此範例會將立方體的面繪製為不同的模型以便稍後對每個面套用不同的紋理。  
  
 [!code-csharp[3doverview#3DOverview3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>   
## <a name="applying-materials-to-the-model"></a>對模型套用材質  
  
 若要讓網格看起來像三維物件，就必須套用紋理以涵蓋由其頂點和三角形所定義的表面，讓觀景窗可以點亮並投影表面。 在[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)]，您使用<xref:System.Windows.Media.Brush>類別，以套用至螢幕的區域的色彩、 圖樣、 漸層或其他視覺內容。  不過，[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 物件的外觀是光源模型的函式，而不只是對物件套用的色彩或圖樣。 真實的物體會根據物體表面的質地以不同方式反射光線︰光滑而閃亮的表面看起來會與粗糙或黯淡的表面不同，而一些物體看起來會吸收光線，一些物體則會發亮。 可對 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 物件套用的所有筆刷都可對 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 物件套用，但是您無法直接套用。  
  
 若要定義模型的介面的特性[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用<xref:System.Windows.Media.Media3D.Material>抽象類別。 Material 的具體子類別會決定模型表面的一些外觀特性，每個特性也提供您可以傳遞 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 屬性。  
  
-   <xref:System.Windows.Media.Media3D.DiffuseMaterial> 指定模型將套用的筆刷，如同該模型已擴散光源。 使用 DiffuseMaterial 非常類似直接對 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 模型使用筆刷；模型表面不會反射光線但看起來閃亮。  
  
-   <xref:System.Windows.Media.Media3D.SpecularMaterial> 指定的筆刷將會套用至模型好像模型的介面是硬式或閃亮、 能夠反映會反白顯示。 您可以藉由指定的值設定這個反光的品質或 「 下雨，"，紋理會提供建議的程度<xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A>屬性。  
  
-   <xref:System.Windows.Media.Media3D.EmissiveMaterial> 可讓您指定將套用紋理，如同模型已發出等於的筆刷色彩。 這不會讓模型變成光源。不過，這會影響陰影處理的方式，與透過 DiffuseMaterial 或 SpecularMaterial 加上紋理的方式不同。  
  
 為提升效能的 backfaces <xref:System.Windows.Media.Media3D.GeometryModel3D> （這些超出檢視的因為它們是從相機模型的另一端的表面） 下列來自窗定位在場景。  若要指定<xref:System.Windows.Media.Media3D.Material>要套用至平面像模型的 backface，設定模型的<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>屬性。  
  
 若要達到某些表面質地，例如發光或反射效果，您可以對模型連續套用數種不同的筆刷。 您可以套用，並重複使用多個材質<xref:System.Windows.Media.Media3D.MaterialGroup>類別。 在多個轉譯階段中，會從頭到尾套用 MaterialGroup 的子系。  
  
 下列程式碼範例示範如何對 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 模型以筆刷的方式套用純色和繪圖。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  
 [!code-xaml[3doverview#3DOverview3DN9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
  
 [!code-csharp[3doverview#3DOverview3DN8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
 [!code-vb[3doverview#3DOverview3DN8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>   
## <a name="illuminating-the-scene"></a>場景照明  
 [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 圖形中的光線運作方式和真實世界的光線相同︰讓表面看得見。 而且，光線還會決定投影時要包含場景的哪個部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光線物件會建立各種光線和陰影效果，而且會仿照真實世界各種光線的行為。 您在場景中必須至少包含一種光線，否則會看不到模型。  
  
 衍生自基底類別的下列燈號<xref:System.Windows.Media.Media3D.Light>:  
  
-   <xref:System.Windows.Media.Media3D.AmbientLight>： 提供周遭光線照亮一致的方式，不論其位置或方向的所有物件。  
  
-   <xref:System.Windows.Media.Media3D.DirectionalLight>： 光線照亮遠的光線來源類似。  具有方向性的燈號<xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A>指定為 Vector3D，但沒有指定的位置。  
  
-   <xref:System.Windows.Media.Media3D.PointLight>： 光線照亮像附近的光源。 PointLights 有一個位置，並從該位置投射光線。 場景中的物件會根據其相對於光線的位置和距離來照明。 <xref:System.Windows.Media.Media3D.PointLightBase> 公開<xref:System.Windows.Media.Media3D.PointLightBase.Range%2A>屬性，決定超過此模型將不會以醒目顯示光線所的距離。 PointLight 也公開衰減屬性，決定光線強度如何隨距離而降低。 您可以為光線衰減指定常數、線性插補或二次插補。  
  
-   <xref:System.Windows.Media.Media3D.SpotLight>： 繼承自<xref:System.Windows.Media.Media3D.PointLight>。 Spotlight 照明的方式類似 PointLight，而且有位置和方向兩者。 在專案中所設定的圓錐形區域 light<xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A>和<xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A>以度為單位指定的屬性。  
  
 燈號都<xref:System.Windows.Media.Media3D.Model3D>物件，讓您可以轉換，並以動畫顯示淺色屬性，包括位置、 色彩、 方向和範圍。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>   
## <a name="transforming-models"></a>轉換模型  
 當您建立模型時，模型在場景中有特定的位置。 若要在場景中四處移動模型、旋轉模型，或變更模型的大小，變更定義模型的頂點本身並不實用。  而是要像在 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 一樣，對模型套用轉換。  
  
 每個模型物件都有<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>與其移動、 重新導向，或調整模型的屬性。  當您套用轉換時，可以透過轉換所指定的任何向量或值，有效率地位移模型的所有點。 換句話說，您已經轉換定義模型所在的座標空間 (「模型空間」)，但尚未變更在整個場景的座標系統 (「世界空間」) 中組成模型幾何的值。  
  
 如需轉換模型的詳細資訊，請參閱 [3D 轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)。  
  
<a name="animations"></a>   
## <a name="animating-models"></a>以動畫顯示模型  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] 實作參與和 [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] 圖形相同的計時和動畫系統。 換句話說，若要以動畫顯示 3D 場景，就要以動畫顯示其模型的屬性。 您可以直接以動畫顯示基元的屬性，但是以動畫顯示變更模型位置或外觀的轉換通常更容易。 因為可以將轉換套用至<xref:System.Windows.Media.Media3D.Model3DGroup>物件以及個別的模型，便可適用於 Model3DGroup 的子系和另一組動畫之子物件的群組的一組動畫。 您也可以以動畫顯示場景光線的屬性，達到各種視覺效果。 最後，您還可以選擇以動畫顯示觀景窗的位置或視野，以動畫顯示投影本身。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 計時和動畫系統的背景資訊，請參閱[動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)、[分鏡腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)，以及 [Freezable 物件概觀](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)等主題。  
  
 若要以動畫顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的物件，您要建立時間軸、定義動畫 (這實際上是某些屬性值隨時間的變化)，並指定要套用動畫的屬性。 因為中的所有物件[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]場景會的子系<xref:System.Windows.Controls.Viewport3D>，任何您想要套用至場景的動畫的目標屬性是 Viewport3D 的內容屬性。  
  
 假設您想要讓模型就地搖晃。 您可以選擇套用<xref:System.Windows.Media.Media3D.RotateTransform3D>模型，並以動畫顯示到另一個向量其旋轉的軸。 下列程式碼範例示範如何對轉換之 Rotation3D 的 Axis 屬性套用 Vector3DAnimation，假設 RotateTransform3D 是要使用 TransformGroup 對模型套用的其中一個轉換。  
  
 [!code-csharp[3doverview#3DOverview3DN1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>   
## <a name="add-3-d-content-to-the-window"></a>在視窗中新增 3D 內容  
 若要呈現的場景，將模型和燈號<xref:System.Windows.Media.Media3D.Model3DGroup>，然後設定<xref:System.Windows.Media.Media3D.Model3DGroup>為<xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A>的<xref:System.Windows.Media.Media3D.ModelVisual3D>。 新增<xref:System.Windows.Media.Media3D.ModelVisual3D>至<xref:System.Windows.Controls.Viewport3D.Children%2A>集合<xref:System.Windows.Controls.Viewport3D>。 新增攝影機<xref:System.Windows.Controls.Viewport3D>藉由設定其<xref:System.Windows.Controls.Viewport3D.Camera%2A>屬性。  
  
 最後，會加入<xref:System.Windows.Controls.Viewport3D>至視窗。 當<xref:System.Windows.Controls.Viewport3D>畫布，例如版面配置項目的內容設定指定 Viewport3D 的大小就會包含其<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>屬性 (繼承自<xref:System.Windows.FrameworkElement>)。  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Viewport3D>  
 <xref:System.Windows.Media.Media3D.PerspectiveCamera>  
 <xref:System.Windows.Media.Media3D.DirectionalLight>  
 <xref:System.Windows.Media.Media3D.Material>  
 [立體轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/3-d-transformations-overview.md)  
 [最大化 WPF 3D 效能](../../../../docs/framework/wpf/graphics-multimedia/maximize-wpf-3d-performance.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-how-to-topics.md)  
 [WPF 中圖案和基本繪圖概觀](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [使用影像、繪圖和視覺效果繪製](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
