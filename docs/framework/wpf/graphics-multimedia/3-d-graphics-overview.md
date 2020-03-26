---
title: 3D 圖形概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291810"
---
# <a name="3d-graphics-overview"></a>3D 圖形概述
<a name="introduction"></a>中的[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]3D 功能使開發人員能夠在標記和程式碼中繪製、轉換和設置 3D 圖形的動畫。 開發人員可以組合 2D 和 3D 圖形以創建豐富的控制項、提供複雜的資料插圖或增強應用程式介面的使用者體驗。 3D[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]支援不是旨在提供功能齊全的遊戲開發平臺。 本主題概述了圖形系統中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D 功能。  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>2D 容器中的 3D  
 中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D 圖形內容封裝在可以參與二<xref:System.Windows.Controls.Viewport3D>維元素結構的元素中。 圖形系統像<xref:System.Windows.Controls.Viewport3D>中的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]許多其他元素一樣被視為二維視覺元素。 <xref:System.Windows.Controls.Viewport3D>作為視窗（視口）進入三維場景。 更準確地說，它是投影 3D 場景的曲面。  
  
 在傳統的 2D 應用程式中，<xref:System.Windows.Controls.Viewport3D>使用另一個容器元素（如網格或畫布）時，將一樣使用。  儘管可以在同一<xref:System.Windows.Controls.Viewport3D>場景圖中與其他 2D 繪圖物件一起使用，但不能在 中<xref:System.Windows.Controls.Viewport3D>滲透 2D 和 3D 物件。  本主題將重點介紹如何在 中<xref:System.Windows.Controls.Viewport3D>繪製 3D 圖形。  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>3D 座標空間  
 2D 圖形的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]坐標系定位渲染區域左上角的原點（通常是螢幕）。 在 2D 系統中，正 X 軸值向右，正 y 軸值向下。  但是，在 3D 坐標系中，原點位於渲染區域的中心，正 X 軸值向右移動，但正 y 軸值則朝上，正 Z 軸值從原點向外移動，對檢視器。  
  
 ![座標系統](./media/coordsystem-1.png "庫德系統-1")  
傳統的 2D 和 3D 坐標系表示  
  
 這些軸定義的空間是 中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]3D 物件的固定參考框架。 當您在此空間中建置模型，並建立光線和觀景窗來檢視這些模型時，有助於區分此靜態參考座標系 (或稱為「世界空間」) 與您為每個模型套用轉換時建立的當地參考座標系。 也請記住，在世界空間中的物件取決於光線和觀景窗設定，可能看起來完全不同，或者完全無法看見，但觀景窗的位置不會改變世界空間中物件的位置。  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>觀景窗和投影  
 使用 2D 工作的開發人員習慣于在二維螢幕上定位繪圖基元。 創建 3D 場景時，請務必記住，您確實在創建 3D 物件的 2D 表示形式。 由於 3D 場景的外觀因旁觀者的觀點而異，因此必須指定該視圖。 該<xref:System.Windows.Media.Media3D.Camera>類允許您為 3D 場景指定此視圖。  
  
 瞭解 3D 場景在 2D 表面上的表示方式的另一種方法是將場景描述為投影到查看表面上。 <xref:System.Windows.Media.Media3D.ProjectionCamera>允許您指定不同的投影及其屬性，以更改旁觀者看到 3D 模型的方式。 指定<xref:System.Windows.Media.Media3D.PerspectiveCamera>預測使場景縮短。  換句話說，提供<xref:System.Windows.Media.Media3D.PerspectiveCamera>消失點透視。  您可以指定觀景窗在場景座標空間中的位置、觀景窗的方向和視野，以及定義場景中「向上」方向的向量。 下圖說明瞭<xref:System.Windows.Media.Media3D.PerspectiveCamera>的投影。  
  
 限制<xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>攝像機<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>投影範圍<xref:System.Windows.Media.Media3D.ProjectionCamera>的 和 屬性。 由於觀景窗可能會位在場景中的任何地方，觀景窗有可能實際上就位在模型內部或非常靠近模型，因此更難正確區分物件。  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>允許您指定與攝像機的最小距離，超出該距離，這樣物件就不會繪製。  相反，<xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A>允許您指定與攝像機的距離，超出該距離，這樣物件就不會繪製，這可確保距離太遠而無法識別的物件不會包含在場景中。  
  
 ![觀景窗設定](./media/coordsystem-6.png "庫德系統-6")  
觀景窗位置  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>指定 3D 模型到 2D 視覺表面的正交投影。 與其他觀景窗相同，它會指定位置、檢視方向和「向上」方向。 但是<xref:System.Windows.Media.Media3D.PerspectiveCamera>，<xref:System.Windows.Media.Media3D.OrthographicCamera>與 描述不包括透視預縮短的投影不同。 換句話說，<xref:System.Windows.Media.Media3D.OrthographicCamera>描述一個視圖框的兩側是平行的，而不是一個側面在攝像機的點中相遇的。 下圖顯示了使用<xref:System.Windows.Media.Media3D.PerspectiveCamera>和<xref:System.Windows.Media.Media3D.OrthographicCamera>查看的相同模型。  
  
 ![正視投影和透視投影](./media/camera-projections4.png "Camera_projections4")  
透視投影和正視投影  
  
 下列程式碼示範一些典型的觀景窗設定。  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>模型和網格基元  
  
 <xref:System.Windows.Media.Media3D.Model3D>是表示泛型 3D 物件的抽象基類。 要構建 3D 場景，需要查看一些物件，構成場景圖的物件派生自<xref:System.Windows.Media.Media3D.Model3D>。 目前，支援[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用 對幾何體<xref:System.Windows.Media.Media3D.GeometryModel3D>進行建模。 此<xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A>模型的屬性採用網格基元。  
  
 若要建立模型，請先建立基元 (也就是網格)。 3D 基本類型是形成單一 3D 實體的頂點集合。 大多數 3D 系統提供以最簡單的閉合圖建模的原始元：由三個頂點定義的三角形。  因為三角形的三個點共面，所以您可以持續加入三角形，以塑造出更複雜的圖形 (稱為網格)。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 3D 系統當前提供類<xref:System.Windows.Media.Media3D.MeshGeometry3D>，允許您指定任何幾何體;它當前不支援預定義的 3D 基元，如球體和立方形式。 通過指定三<xref:System.Windows.Media.Media3D.MeshGeometry3D>角形頂點清單作為其<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>屬性，開始創建 。 每個頂點指定為<xref:System.Windows.Media.Media3D.Point3D>。  （在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]中，將此屬性指定為以三為單位的表示每個頂點的座標的數位的清單。根據其幾何體，網格可能由許多三角形組成，其中一些三角形共用相同的角（頂點）。 若要正確繪製網格，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 需要哪些三角形共用哪些頂點的相關資訊。 通過指定具有 屬性的三角形索引清單來<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>提供此資訊。 此清單指定<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單中指定的點將確定三角形的順序。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 在前面的示例中，<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單指定八個頂點來定義立方體形狀的網格。 屬性<xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>指定十二組三個索引的清單。  清單中的每個數位都引用清單中的<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>偏移量。  例如，<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單指定的前三個頂點是 （1，1，0）、（0，1，0）和 （0，0，0）。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A>清單指定的前三個索引是 0、2 和 1，它們對應于<xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A>清單中的第一點、第三個點和第二個點。 因此，組成立方體模型的第一個三角形將會從 (1,1,0) 到 (0,1,0) 到 (0,0,0) 組成，其餘的十一個三角形也同樣如此決定。  
  
 可以通過指定 和<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A><xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>屬性的值來繼續定義模型。  若要轉譯模型的表面，圖形系統需要表面在任意指定的三角形處面對哪個方向的資訊。 系統會使用此資訊來進行模型的光線計算︰直接面向光源的表面看起來就會比偏離光線一些角度的表面還亮。 雖然 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以使用位置座標決定預設的法向向量，但是您也可以指定不同的法向向量以模擬曲面的外觀。  
  
 屬性<xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>指定一個<xref:System.Windows.Point>s 集合，告訴圖形系統如何映射確定紋理如何繪製到網格頂點的座標。 <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>指定為介於零和 1 之間的值，包括。  與<xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A>屬性一樣，圖形系統可以計算預設紋理座標，但您可以選擇設置不同的紋理座標，以控制包含重複圖案的一部分的紋理的映射。例如。 您可以在後續的主題或 Managed Direct3D SDK 中找到有關紋理座標的詳細資訊。  
  
 下列範例示範如何以程序性程式碼建立立方體模型的一個面。 您可以將整個立方體繪製為單個幾何模型3D;但是，您可以將整個立方體繪製為單個幾何模型3D。本示例將立方體的面繪製為不同的模型，以便以後將單獨的紋理應用於每個面。  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>對模型套用材質  
  
 若要讓網格看起來像三維物件，就必須套用紋理以涵蓋由其頂點和三角形所定義的表面，讓觀景窗可以點亮並投影表面。 在 2D 中，<xref:System.Windows.Media.Brush>使用 類將顏色、圖案、漸變或其他視覺內容應用於螢幕區域。  但是，3D 物件的外觀是照明模型的函數，而不僅僅是應用於它們的顏色或圖案的函數。 真實的物體會根據物體表面的質地以不同方式反射光線︰光滑而閃亮的表面看起來會與粗糙或黯淡的表面不同，而一些物體看起來會吸收光線，一些物體則會發亮。 您可以將所有相同的畫筆應用於可應用於 2D 物件的 3D 物件，但不能直接應用它們。  
  
 要定義模型曲面的特徵，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]請使用<xref:System.Windows.Media.Media3D.Material>抽象類別。 Material 的具體子類別會決定模型表面的一些外觀特性，每個特性也提供您可以傳遞 SolidColorBrush、TileBrush 或 VisualBrush 的 Brush 屬性。  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>指定畫筆將應用於模型，就像模型被漫射一樣。 使用漫反射材質最類似于直接在 2D 模型上使用畫筆;模型表面不會反射光線，如光澤。  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>指定畫筆將應用於模型，就像模型的表面是堅硬的或有光澤的，能夠反射高光。 您可以通過指定<xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A>屬性的值來設置紋理將建議此反射品質或"光澤"的程度。  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>允許您指定紋理將應用，就像模型發出的光等於畫筆的顏色一樣。 這不會讓模型變成光源。不過，這會影響陰影處理的方式，與透過 DiffuseMaterial 或 SpecularMaterial 加上紋理的方式不同。  
  
 為了更好的性能，從場景中剔除<xref:System.Windows.Media.Media3D.GeometryModel3D>a 的背面（那些由於位於相機模型的另一側而偏離視圖的面）。  要指定<xref:System.Windows.Media.Media3D.Material>要應用於模型的背面（如平面），請設置模型的屬性<xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A>。  
  
 若要達到某些表面質地，例如發光或反射效果，您可以對模型連續套用數種不同的筆刷。 您可以使用<xref:System.Windows.Media.Media3D.MaterialGroup>類應用和重用多個材質。 在多個轉譯階段中，會從頭到尾套用 MaterialGroup 的子系。  
  
 以下代碼示例演示如何將純色和繪圖作為畫筆應用於 3D 模型。  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>場景照明  
 3D 圖形中的燈光可以像燈光在現實世界中一起做什麼：它們使曲面可見。 而且，光線還會決定投影時要包含場景的哪個部分。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的光線物件會建立各種光線和陰影效果，而且會仿照真實世界各種光線的行為。 場景中至少包含一個燈光，否則看不到任何模型。  
  
 以下燈光派生自基類<xref:System.Windows.Media.Media3D.Light>：  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>： 提供環境照明，無論所有物件的位置或方向如何，都能均勻地照亮所有物件。  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>：像遠處的光源一樣發光。  方向燈光指定<xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A>為 Vector3D，但沒有指定的位置。  
  
- <xref:System.Windows.Media.Media3D.PointLight>：像附近的光源一樣發光。 PointLights 有一個位置，並從該位置投射光線。 場景中的物件會根據其相對於光線的位置和距離來照明。 <xref:System.Windows.Media.Media3D.PointLightBase>公開屬性<xref:System.Windows.Media.Media3D.PointLightBase.Range%2A>，該屬性確定模型不會被光線照亮的距離。 PointLight 還公開衰減屬性，這些衰減屬性決定了光線的強度在距離上是如何減小的。 您可以為光線衰減指定常數、線性插補或二次插補。  
  
- <xref:System.Windows.Media.Media3D.SpotLight>：從<xref:System.Windows.Media.Media3D.PointLight>繼承。 Spotlight 照明的方式類似 PointLight，而且有位置和方向兩者。 它們在由<xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A>和<xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A>屬性設置的錐形區域中投射光線，以度為單位指定。  
  
 燈光是<xref:System.Windows.Media.Media3D.Model3D>物件，因此您可以變換和設置燈光屬性的動畫，包括位置、顏色、方向和範圍。  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>轉換模型  
 當您建立模型時，模型在場景中有特定的位置。 若要在場景中四處移動模型、旋轉模型，或變更模型的大小，變更定義模型的頂點本身並不實用。  相反，就像在 2D 中一樣，您將變換應用於模型。  
  
 每個模型物件都有一<xref:System.Windows.Media.Media3D.Model3D.Transform%2A>個屬性，您可以使用該屬性移動、調整方向或調整模型的大小。  當您套用轉換時，可以透過轉換所指定的任何向量或值，有效率地位移模型的所有點。 換句話說，您已經轉換定義模型所在的座標空間 (「模型空間」)，但尚未變更在整個場景的座標系統 (「世界空間」) 中組成模型幾何的值。  
  
 有關變換模型的詳細資訊，請參閱[3D 變換概述](3-d-transformations-overview.md)。  
  
<a name="animations"></a>
## <a name="animating-models"></a>以動畫顯示模型  
 3D[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實現與 2D 圖形參與相同的計時和動畫系統。 換句話說，要為 3D 場景設置動畫，為其模型的屬性設置動畫。 您可以直接以動畫顯示基元的屬性，但是以動畫顯示變更模型位置或外觀的轉換通常更容易。 由於轉換可以應用於<xref:System.Windows.Media.Media3D.Model3DGroup>物件以及單個模型，因此可以將一組動畫應用於 Model3DGroup 的子級動畫，將另一組動畫應用於一組子物件。 您也可以以動畫顯示場景光線的屬性，達到各種視覺效果。 最後，您還可以選擇以動畫顯示觀景窗的位置或視野，以動畫顯示投影本身。 如需 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 計時和動畫系統的背景資訊，請參閱[動畫概觀](animation-overview.md)、[分鏡腳本概觀](storyboards-overview.md)，以及 [Freezable 物件概觀](../advanced/freezable-objects-overview.md)等主題。  
  
 若要以動畫顯示 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的物件，您要建立時間軸、定義動畫 (這實際上是某些屬性值隨時間的變化)，並指定要套用動畫的屬性。 由於 3D 場景中的所有物件都是 的<xref:System.Windows.Controls.Viewport3D>子物件，因此要應用於該場景的任何動畫的目標屬性都是 Viewport3D 的屬性。  
  
 假設您想要讓模型就地搖晃。 您可以選擇對模型應用 ，<xref:System.Windows.Media.Media3D.RotateTransform3D>並為其旋轉軸從一個向量到另一個向量設置動畫。 下列程式碼範例示範如何對轉換之 Rotation3D 的 Axis 屬性套用 Vector3DAnimation，假設 RotateTransform3D 是要使用 TransformGroup 對模型套用的其中一個轉換。  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>將 3D 內容添加到視窗  
 要渲染場景，將模型和燈光添加到<xref:System.Windows.Media.Media3D.Model3DGroup>中，然後將<xref:System.Windows.Media.Media3D.Model3DGroup>設置為<xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> <xref:System.Windows.Media.Media3D.ModelVisual3D>。 將<xref:System.Windows.Media.Media3D.ModelVisual3D>添加到<xref:System.Windows.Controls.Viewport3D.Children%2A>集合 中<xref:System.Windows.Controls.Viewport3D>。 通過設置其<xref:System.Windows.Controls.Viewport3D.Camera%2A>屬性<xref:System.Windows.Controls.Viewport3D>將攝像機添加到 。  
  
 最後，將<xref:System.Windows.Controls.Viewport3D>添加到視窗中。 當<xref:System.Windows.Controls.Viewport3D>包含在 佈局元素（如 Canvas）的內容時，通過設置其<xref:System.Windows.FrameworkElement.Height%2A>和<xref:System.Windows.FrameworkElement.Width%2A>屬性（繼承自<xref:System.Windows.FrameworkElement>） 來指定 Viewport3D 的大小。  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [3D 轉換概述](3-d-transformations-overview.md)
- [最大化 WPF 3D 效能](maximize-wpf-3d-performance.md)
- [如何使用主題](3-d-graphics-how-to-topics.md)
- [WPF 中圖案和基本繪圖概觀](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用影像、繪圖和視覺效果繪製](painting-with-images-drawings-and-visuals.md)
