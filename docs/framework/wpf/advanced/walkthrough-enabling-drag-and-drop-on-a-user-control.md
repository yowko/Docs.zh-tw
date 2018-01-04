---
title: "逐步解說：在使用者控制項上啟用拖放功能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e413a7ddf7e256538e56876712a54f875392b59a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>逐步解說：在使用者控制項上啟用拖放功能
本逐步解說示範如何建立自訂使用者控制項以參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的拖放資料傳輸。  
  
 在本逐步解說，您將建立自訂 WPF<xref:System.Windows.Controls.UserControl>代表圓形。 您將在控制項上實作功能，以啟用透過拖放的資料傳輸。 例如，如果您從某個 Circle 控制項拖曳至另一個 Circle 控制項，則會將填滿色彩資料從來源 Circle 複製至目標。 如果您從圓形控制項拖曳<xref:System.Windows.Controls.TextBox>，填滿色彩的字串表示會複製到<xref:System.Windows.Controls.TextBox>。 您也會建立包含兩個面板控制項的小型應用程式和<xref:System.Windows.Controls.TextBox>測試拖放功能。 您將撰寫讓面板處理所置放 Circle 資料的程式碼，以讓您將 Circle 從某個面版的子系集合移動或複製至另一個面板。  
  
 這個逐步解說將說明下列工作：  
  
-   建立自訂使用者控制項。  
  
-   可讓使用者控制項成為拖曳來源。  
  
-   讓使用者控制項成為置放目標。  
  
-   啟用面板，以接收從使用者控制項置放的資料。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   Visual Studio 2010  
  
## <a name="creating-the-application-project"></a>建立應用程式專案  
 在本節中，您將建立應用程式基礎結構，其中包含具有兩個面板的主頁面和<xref:System.Windows.Controls.TextBox>。  
  
### <a name="to-create-the-project"></a>若要建立專案  
  
1.  在 Visual Basic 或 Visual C# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。 如需詳細資訊，請參閱[如何：建立新的 WPF 應用程式專案](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82)。  
  
2.  開啟 MainWindow.xaml。  
  
3.  加入下列標記的開頭和結尾之間<xref:System.Windows.Controls.Grid>標記。  
  
     此標記會建立測試應用程式的使用者介面。  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]  
  
## <a name="adding-a-new-user-control-to-the-project"></a>將新的使用者控制項新增至專案  
 在本節中，您會將新的使用者控制項新增至專案。  
  
### <a name="to-add-a-new-user-control"></a>新增使用者控制項  
  
1.  在 [專案] 功能表上，選取 [新增使用者控制項]。  
  
2.  在 [新增項目] 對話方塊中，將名稱變更為 `Circle.xaml`，然後按一下 [新增]。  
  
     Circle.xaml 和其程式碼後置會新增至專案。  
  
3.  開啟 Circle.xaml。  
  
     此檔案將包含使用者控制項的使用者介面項目。  
  
4.  將下列標記加入至根<xref:System.Windows.Controls.Grid>建立簡單的使用者控制項具有為其 UI 的藍色圓形。  
  
     [!code-xaml[DragDropWalkthrough#EllipseXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]  
  
5.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
6.  在 C# 中，於預設建構函式後面新增下列程式碼，以建立複製建構函式。 在 Visual Basic 中，新增下列程式碼，以建立預設建構函式和複製建構函式。  
  
     若要允許複製使用者控制項，您可以在程式碼後置檔案中新增複製建構函式方法。 在簡化 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小。  
  
     [!code-csharp[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]  
  
### <a name="to-add-the-user-control-to-the-main-window"></a>將使用者控制項新增至主要視窗  
  
1.  開啟 MainWindow.xaml。  
  
2.  加入開頭加入下列 XAML<xref:System.Windows.Window>標記來建立目前的應用程式之 XML 命名空間參考。  
  
    ```  
    xmlns:local="clr-namespace:DragDropExample"  
    ```  
  
3.  在第一個<xref:System.Windows.Controls.StackPanel>，加入下列 XAML 建立第一個面板中的圓形使用者控制項的兩個執行個體。  
  
     [!code-xaml[DragDropWalkthrough#CirclesXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]  
  
     面板的完整 XAML 如下。  
  
     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]  
  
## <a name="implementing-drag-source-events-in-the-user-control"></a>在使用者控制項中實作拖曳來源事件  
 在本節中，您將會覆寫<xref:System.Windows.UIElement.OnMouseMove%2A>方法，並起始拖放作業。  
  
 如果已啟動拖曳 （按下滑鼠按鈕並在移動滑鼠），您將封裝資料傳輸至<xref:System.Windows.DataObject>。 在此情況下，Circle 控制項將會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。  
  
### <a name="to-initiate-a-drag-and-drop-operation"></a>啟始拖放作業  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.MouseMove>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]  
  
     這<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫會執行下列工作：  
  
    -   檢查是否在滑鼠移動時按下滑鼠左鍵。  
  
    -   封裝成的圓形資料<xref:System.Windows.DataObject>。 在此情況下，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。  
  
    -   呼叫靜態<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>方法以啟始拖放作業。 傳遞下列三個參數，<xref:System.Windows.DragDrop.DoDragDrop%2A>方法：  
  
        -   `dragSource` – 此控制項的參考。  
  
        -   `data`–<xref:System.Windows.DataObject>在先前的程式碼中建立。  
  
        -   `allowedEffects`– 在允許的拖放作業，也就是<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。  
  
3.  按 F5 鍵建置並執行應用程式。  
  
4.  按一下其中一個圓形控制項和拖曳的面板，其他的圓形，而<xref:System.Windows.Controls.TextBox>。 當拖曳到<xref:System.Windows.Controls.TextBox>，游標會變更以表示移動。  
  
5.  拖曳 Circle 時<xref:System.Windows.Controls.TextBox>，請按住 CTRL 鍵。 請注意，游標變更以指出正在進行複製。  
  
6.  將拖放到圓形<xref:System.Windows.Controls.TextBox>。 Circle 之填滿色彩的字串表示附加至<xref:System.Windows.Controls.TextBox>。  
  
     ![Circle 之填滿色彩的字串表示](../../../../docs/framework/wpf/advanced/media/dragdrop-colorstring.png "DragDrop_ColorString")  
  
 根據預設，游標會在拖放作業期間變更，表示置放資料的效果。 您可以自訂處理所提供給使用者的意見反應<xref:System.Windows.UIElement.GiveFeedback>事件，以及設定不同的資料指標。  
  
### <a name="to-give-feedback-to-the-user"></a>提供使用者的意見反應  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.GiveFeedback>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]  
  
     這<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫會執行下列工作：  
  
    -   檢查<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>置放目標中所設定的值<xref:System.Windows.UIElement.DragOver>事件處理常式。  
  
    -   設定自訂游標，根據<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>值。 游標用於將資料置放效果的視覺化回饋提供給使用者。  
  
3.  按 F5 鍵建置並執行應用程式。  
  
4.  其中一個圓形控制面板圓形，拖曳和<xref:System.Windows.Controls.TextBox>。 請注意，資料指標現在是您在中指定自訂游標<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫。  
  
     ![以自訂游標執行拖放作業](../../../../docs/framework/wpf/advanced/media/dragdrop-customcursor.png "DragDrop_CustomCursor")  
  
5.  選取的文字`green`從<xref:System.Windows.Controls.TextBox>。  
  
6.  將 `green` 文字拖曳至 Circle 控制項。 請注意，會顯示預設游標，表示拖放作業的效果。 意見反應游標一律是由拖曳來源所設定。  
  
## <a name="implementing-drop-target-events-in-the-user-control"></a>在使用者控制項中實作置放目標事件  
 在本節中，您將指定使用者控制項是置放目標、覆寫讓使用者控制項成為置放目標的方法，以及處理置放在其上的資料。  
  
### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>讓使用者控制項成為置放目標  
  
1.  開啟 Circle.xaml。  
  
2.  開啟<xref:System.Windows.Controls.UserControl>標記中加入<xref:System.Windows.UIElement.AllowDrop%2A>屬性並將它設定為`true`。  
  
     [!code-xaml[DragDropWalkthrough#UCTagXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]  
  
 <xref:System.Windows.UIElement.OnDrop%2A>方法時，會呼叫<xref:System.Windows.UIElement.AllowDrop%2A>屬性設定為`true`和圓形使用者控制項上卸除資料從拖曳來源。 在此方法中，您將處理置放的資料，並將資料套用至 Circle。  
  
### <a name="to-process-the-dropped-data"></a>處理置放的資料  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列<xref:System.Windows.UIElement.OnDrop%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.Drop>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]  
  
     這<xref:System.Windows.UIElement.OnDrop%2A>覆寫會執行下列工作：  
  
    -   使用<xref:System.Windows.DataObject.GetDataPresent%2A>方法來檢查拖曳的資料是否包含字串物件。  
  
    -   使用<xref:System.Windows.DataObject.GetData%2A>方法，可擷取字串資料，如果有的話。  
  
    -   使用<xref:System.Windows.Media.BrushConverter>嘗試將字串轉換為<xref:System.Windows.Media.Brush>。  
  
    -   如果轉換成功，會套用到筆刷<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>提供圓形控制項的 UI。  
  
    -   標記<xref:System.Windows.UIElement.Drop>為已處理的事件。 您應該將置放事件標示為已處理，讓收到此事件的其他項目知道 Circle 使用者控制項已處理過它。  
  
3.  按 F5 鍵建置並執行應用程式。  
  
4.  選取的文字`green`中<xref:System.Windows.Controls.TextBox>。  
  
5.  將文字拖放至 Circle 控制項。 Circle 會從藍色變成綠色。  
  
     ![將字串轉換成筆刷](../../../../docs/framework/wpf/advanced/media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")  
  
6.  輸入的文字`green`中<xref:System.Windows.Controls.TextBox>。  
  
7.  選取的文字`gre`中<xref:System.Windows.Controls.TextBox>。  
  
8.  將它拖放至 Circle 控制項。 請注意，游標變更以指出允許置放，但 Circle 的色彩不會變更，因為 `gre` 不是有效的色彩。  
  
9. 從綠色 Circle 控制項拖放至藍色 Circle 控制項。 Circle 會從藍色變成綠色。 請注意，顯示的游標取決於是否<xref:System.Windows.Controls.TextBox>或圓形是拖曳來源。  
  
 設定<xref:System.Windows.UIElement.AllowDrop%2A>屬性`true`和處理的已卸除的資料都只需要啟用要在置放目標項目。 不過，若要提供較佳使用者體驗，您應該也處理<xref:System.Windows.UIElement.DragEnter>， <xref:System.Windows.UIElement.DragLeave>，和<xref:System.Windows.UIElement.DragOver>事件。 在這些事件中，您可以在置放資料之前執行檢查，並將其他意見反應提供給使用者。  
  
 將資料拖曳至 Circle 使用者控制項上方時，控制項應該通知拖曳來源是否可以處理所拖曳的資料。 如果控制項不知道如何處理資料，則應該拒絕置放。 若要這樣做，您將處理<xref:System.Windows.UIElement.DragOver>事件以及組<xref:System.Windows.DragEventArgs.Effects%2A>屬性。  
  
### <a name="to-verify-that-the-data-drop-is-allowed"></a>確認允許資料置放  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  加入下列<xref:System.Windows.UIElement.OnDragOver%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.DragOver>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]  
  
     這<xref:System.Windows.UIElement.OnDragOver%2A>覆寫會執行下列工作：  
  
    -   將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。  
  
    -   執行中執行相同的檢查<xref:System.Windows.UIElement.OnDrop%2A>方法，以判斷圓形使用者控制是否可以處理拖曳的資料。  
  
    -   如果使用者控制項可以處理資料，設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。  
  
3.  按 F5 鍵建置並執行應用程式。  
  
4.  選取的文字`gre`中<xref:System.Windows.Controls.TextBox>。  
  
5.  將文字拖曳至 Circle 控制項。 請注意，游標現在會變更以指出不允許置放，因為 `gre` 不是有效的色彩。  
  
 您可以套用置放作業的預覽，進一步增強使用者體驗。 圓形使用者控制項，您將會覆寫<xref:System.Windows.UIElement.OnDragEnter%2A>和<xref:System.Windows.UIElement.OnDragLeave%2A>方法。 當資料拖曳到橢圓形上的控制項，目前的背景<xref:System.Windows.Shapes.Shape.Fill%2A>儲存預留位置變數中。 然後轉換成筆刷並套用至字串<xref:System.Windows.Shapes.Ellipse>提供為圓形的 UI。 如果資料但不置放、 原始拖出圓形<xref:System.Windows.Shapes.Shape.Fill%2A>值重新套用至圓形。  
  
### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>預覽拖放作業的效果  
  
1.  開啟 Circle.xaml.cs 或 Circle.xaml.vb。  
  
2.  圓形類別中宣告私用<xref:System.Windows.Media.Brush>名為變數`_previousFill`並加以初始化以`null`。  
  
     [!code-csharp[DragDropWalkthrough#Brush](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]  
  
3.  加入下列<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.DragEnter>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]  
  
     這<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫會執行下列工作：  
  
    -   將儲存<xref:System.Windows.Shapes.Shape.Fill%2A>屬性<xref:System.Windows.Shapes.Ellipse>中`_previousFill`變數。  
  
    -   執行中執行相同的檢查<xref:System.Windows.UIElement.OnDrop%2A>方法，以判斷資料是否可以轉換成<xref:System.Windows.Media.Brush>。  
  
    -   如果資料轉換成有效<xref:System.Windows.Media.Brush>，適用於以<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>。  
  
4.  加入下列<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫可提供的類別處理<xref:System.Windows.UIElement.DragLeave>事件。  
  
     [!code-csharp[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]  
  
     這<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫會執行下列工作：  
  
    -   適用於<xref:System.Windows.Media.Brush>存入`_previousFill`變數設為<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Ellipse>提供圓形使用者控制項的 UI。  
  
5.  按 F5 鍵建置並執行應用程式。  
  
6.  選取的文字`green`中<xref:System.Windows.Controls.TextBox>。  
  
7.  將文字拖曳至 Circle 控制項上方，但不置放文字。 Circle 會從藍色變成綠色。  
  
     ![預覽拖放作業的效果](../../../../docs/framework/wpf/advanced/media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")  
  
8.  從 Circle 控制項拖離文字。 Circle 會從綠色變回藍色。  
  
## <a name="enabling-a-panel-to-receive-dropped-data"></a>讓面板接收置放的資料  
 在本節中，您將啟用一些面板，以裝載 Circle 使用者控制項作為所拖曳 Circle 資料的置放目標。 您將實作程式碼，以將 Circle 從某個面板移至另一個面板，或在拖放 Circle 時按住 CTRL 鍵來複製 Circle 控制項。  
  
### <a name="to-enable-the-panel-to-be-a-drop-target"></a>讓面板成為置放目標  
  
1.  開啟 MainWindow.xaml。  
  
2.  下列 XAML，在每個所示<xref:System.Windows.Controls.StackPanel>控制項，加入處理常式<xref:System.Windows.UIElement.DragOver>和<xref:System.Windows.UIElement.Drop>事件。 名稱<xref:System.Windows.UIElement.DragOver>事件處理常式， `panel_DragOver`，並命名<xref:System.Windows.UIElement.Drop>事件處理常式， `panel_Drop`。  
  
     [!code-xaml[DragDropWalkthrough#PanelsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]  
  
3.  開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。  
  
4.  加入下列程式碼<xref:System.Windows.UIElement.DragOver>事件處理常式。  
  
     [!code-csharp[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]  
  
     這<xref:System.Windows.UIElement.DragOver>事件處理常式會執行下列工作：  
  
    -   會檢查拖曳的資料包含封裝中的 「 物件 」 資料<xref:System.Windows.DataObject>圓形使用者控制和呼叫中傳遞<xref:System.Windows.DragDrop.DoDragDrop%2A>。  
  
    -   如果有「物件」資料，請檢查是否按下 CTRL 鍵。  
  
    -   如果按下 CTRL 鍵時，設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性<xref:System.Windows.DragDropEffects.Copy>。 否則，設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性<xref:System.Windows.DragDropEffects.Move>。  
  
5.  加入下列程式碼<xref:System.Windows.UIElement.Drop>事件處理常式。  
  
     [!code-csharp[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]  
  
     這<xref:System.Windows.UIElement.Drop>事件處理常式會執行下列工作：  
  
    -   檢查是否<xref:System.Windows.UIElement.Drop>已處理事件。 比方說，如果圓形已卸除另一個圓圈，其控制代碼<xref:System.Windows.UIElement.Drop>事件，您不想包含也要處理它圓形的面板。  
  
    -   如果<xref:System.Windows.UIElement.Drop>不處理事件，檢查是否按下 CTRL 鍵。  
  
    -   如果按下 CTRL 鍵時<xref:System.Windows.UIElement.Drop>情況發生，控制為圓形的複本，並將它加入<xref:System.Windows.Controls.Panel.Children%2A>集合<xref:System.Windows.Controls.StackPanel>。  
  
    -   如果未按下 CTRL 鍵，將從圓形<xref:System.Windows.Controls.Panel.Children%2A>集合至其父面板<xref:System.Windows.Controls.Panel.Children%2A>所放置的面板集合。  
  
    -   設定<xref:System.Windows.DragEventArgs.Effects%2A>屬性，以通知<xref:System.Windows.DragDrop.DoDragDrop%2A>方法是否執行移動或複製作業。  
  
6.  按 F5 鍵建置並執行應用程式。  
  
7.  選取的文字`green`從<xref:System.Windows.Controls.TextBox>。  
  
8.  將文字拖放至 Circle 控制項。  
  
9. 將 Circle 控制項從從左面板拖放至右面板。 圓形移除了<xref:System.Windows.Controls.Panel.Children%2A>左面板中的集合並加入至子系集合，右方面板。  
  
10. 按下 CTRL 鍵時，將 Circle 控制項從所在的面板拖放至另一個面板。 圓形會複製，而這個複本加入<xref:System.Windows.Controls.Panel.Children%2A>接收面板的集合。  
  
     ![拖曳 Circle 時按住 CTRL 鍵](../../../../docs/framework/wpf/advanced/media/dragdrop-paneldrop.png "DragDrop_PanelDrop")  
  
## <a name="see-also"></a>請參閱  
 [拖放概觀](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
