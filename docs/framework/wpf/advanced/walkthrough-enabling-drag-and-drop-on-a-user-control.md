---
title: 逐步解說：在使用者控制項上啟用拖放功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 80fd55be9230729cb8336be91c1d8fb4f7f3f080
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364259"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>逐步解說：在使用者控制項上啟用拖放功能

本逐步解說示範如何建立自訂使用者控制項以參與 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的拖放資料傳輸。

在此逐步解說中, 您將建立代表<xref:System.Windows.Controls.UserControl>圓形圖形的自訂 WPF。 您將在控制項上實作功能，以啟用透過拖放的資料傳輸。 例如，如果您從某個 Circle 控制項拖曳至另一個 Circle 控制項，則會將填滿色彩資料從來源 Circle 複製至目標。 如果您從 Circle 控制項拖曳至<xref:System.Windows.Controls.TextBox>, 則填滿色彩的字串表示會複製<xref:System.Windows.Controls.TextBox>到。 您也會建立一個包含兩個面板控制項的小型應用程式<xref:System.Windows.Controls.TextBox> , 以及一個測試拖放功能的。 您將撰寫讓面板處理所置放 Circle 資料的程式碼，以讓您將 Circle 從某個面版的子系集合移動或複製至另一個面板。

這個逐步解說將說明下列工作：

- 建立自訂使用者控制項。

- 可讓使用者控制項成為拖曳來源。

- 讓使用者控制項成為置放目標。

- 啟用面板，以接收從使用者控制項置放的資料。

## <a name="prerequisites"></a>必要條件

若要完成這個逐步解說，您必須具有 Visual Studio。

## <a name="create-the-application-project"></a>建立應用程式專案
 在本節中, 您將建立應用程式基礎結構, 其中包含具有兩個面板和的<xref:System.Windows.Controls.TextBox>主頁面。

1. 在 Visual Basic 或 Visual C# 中，建立名為 `DragDropExample` 的新 WPF 應用程式專案。 如需詳細資訊，請參閱[逐步解說：我的第一個 WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)桌面應用程式。

2. 開啟 MainWindow.xaml。

3. 在開頭和結尾<xref:System.Windows.Controls.Grid>標記之間新增下列標記。

     此標記會建立測試應用程式的使用者介面。

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>將新的使用者控制項加入至專案
 在本節中，您會將新的使用者控制項新增至專案。

1. 在 [專案] 功能表上，選取 [新增使用者控制項]  。

2. 在 [**加入新專案**] 對話方塊中, 將名稱變更`Circle.xaml`為, 然後按一下 [**新增**]。

     Circle.xaml 和其程式碼後置會新增至專案。

3. 開啟 Circle.xaml。

     此檔案將包含使用者控制項的使用者介面項目。

4. 將下列標記新增至根<xref:System.Windows.Controls.Grid> , 以建立具有藍色圓圈作為其 UI 的簡單使用者控制項。

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

6. 在C#中, 于無參數的函式後面加入下列程式碼, 以建立複製的函式。 在 Visual Basic 中, 新增下列程式碼, 以建立無參數的函式和複製的函式。

     若要允許複製使用者控制項，您可以在程式碼後置檔案中新增複製建構函式方法。 在簡化 Circle 使用者控制項中，您只會複製使用者控制項的填滿和大小。

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>將使用者控制項加入至主視窗

1. 開啟 MainWindow.xaml。

2. 將下列 XAML 加入至開頭<xref:System.Windows.Window>標記, 以建立目前應用程式的 XML 命名空間參考。

    ```
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. 在第一個<xref:System.Windows.Controls.StackPanel>中, 新增下列 XAML, 在第一個面板中建立 Circle 使用者控制項的兩個實例。

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     面板的完整 XAML 如下。

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>在使用者控制項中執行拖曳來源事件
 在本節中, 您將覆寫<xref:System.Windows.UIElement.OnMouseMove%2A>方法, 並起始拖放作業。

 如果已啟動拖曳 (按下滑鼠按鍵並移動滑鼠), 您將會封裝要傳送至的<xref:System.Windows.DataObject>資料。 在此情況下，Circle 控制項將會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。

### <a name="to-initiate-a-drag-and-drop-operation"></a>啟始拖放作業

1. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

2. 新增下列<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫, 以提供<xref:System.Windows.UIElement.MouseMove>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     此<xref:System.Windows.UIElement.OnMouseMove%2A>覆寫會執行下列工作:

    - 檢查是否在滑鼠移動時按下滑鼠左鍵。

    - 將圓形資料封裝成<xref:System.Windows.DataObject>。 在此情況下，Circle 控制項會封裝三個資料項目：其填滿色彩的字串表示、高度的 double 表示和其本身的複本。

    - 呼叫靜態<xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType>方法, 以起始拖放作業。 您會將下列三個參數傳遞<xref:System.Windows.DragDrop.DoDragDrop%2A>給方法:

        - `dragSource` – 此控制項的參考。

        - `data`–在<xref:System.Windows.DataObject>先前的程式碼中建立的。

        - `allowedEffects`–允許的拖放作業, 也就是<xref:System.Windows.DragDropEffects.Copy>或。 <xref:System.Windows.DragDropEffects.Move>

3. 按 **F5** 鍵建置並執行應用程式。

4. 按一下其中一個 Circle 控制項, 然後將它拖曳至面板、另一個圓形和<xref:System.Windows.Controls.TextBox>。 當拖曳<xref:System.Windows.Controls.TextBox>至時, 游標會變更以表示移動。

5. 將<xref:System.Windows.Controls.TextBox>圓形拖曳到上時, 請按下**Ctrl**鍵。 請注意，游標變更以指出正在進行複製。

6. 將圓形拖放到上<xref:System.Windows.Controls.TextBox>。 圓形填滿色彩的字串表示會附加至<xref:System.Windows.Controls.TextBox>。

     ![Circle 之填滿色彩的字串表示](./media/dragdrop-colorstring.png "DragDrop_ColorString")

根據預設，游標會在拖放作業期間變更，表示置放資料的效果。 您可以藉由處理<xref:System.Windows.UIElement.GiveFeedback>事件並設定不同的資料指標, 自訂提供給使用者的意見反應。

## <a name="give-feedback-to-the-user"></a>將意見反應提供給使用者

1. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

2. 新增下列<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫, 以提供<xref:System.Windows.UIElement.GiveFeedback>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     此<xref:System.Windows.UIElement.OnGiveFeedback%2A>覆寫會執行下列工作:

    - 檢查在放置目標的<xref:System.Windows.UIElement.DragOver>事件處理常式中設定的值。<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>

    - 根據<xref:System.Windows.GiveFeedbackEventArgs.Effects%2A>值設定自訂資料指標。 游標用於將資料置放效果的視覺化回饋提供給使用者。

3. 按 **F5** 鍵建置並執行應用程式。

4. 將其中一個 Circle 控制項拖曳至面板、另一個圓形和<xref:System.Windows.Controls.TextBox>。 請注意, 資料指標現在是您在覆<xref:System.Windows.UIElement.OnGiveFeedback%2A>寫中指定的自訂資料指標。

     ![以自訂游標執行拖放作業](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. `green` 選取<xref:System.Windows.Controls.TextBox>中的文字。

6. 將 `green` 文字拖曳至 Circle 控制項。 請注意，會顯示預設游標，表示拖放作業的效果。 意見反應游標一律是由拖曳來源所設定。

## <a name="implement-drop-target-events-in-the-user-control"></a>在使用者控制項中執行放置目標事件
 在本節中，您將指定使用者控制項是置放目標、覆寫讓使用者控制項成為置放目標的方法，以及處理置放在其上的資料。

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>讓使用者控制項成為置放目標

1. 開啟 Circle.xaml。

2. 在開頭<xref:System.Windows.Controls.UserControl>標記中, <xref:System.Windows.UIElement.AllowDrop%2A>新增屬性, 並將它設定`true`為。

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

當屬性設定為`true`時, 會呼叫方法,並將拖曳來源的資料放在Circle使用者控制項上。<xref:System.Windows.UIElement.OnDrop%2A> <xref:System.Windows.UIElement.AllowDrop%2A> 在此方法中，您將處理置放的資料，並將資料套用至 Circle。

### <a name="to-process-the-dropped-data"></a>處理置放的資料

1. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

2. 新增下列<xref:System.Windows.UIElement.OnDrop%2A>覆寫, 以提供<xref:System.Windows.UIElement.Drop>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     此<xref:System.Windows.UIElement.OnDrop%2A>覆寫會執行下列工作:

    - <xref:System.Windows.DataObject.GetDataPresent%2A>使用方法來檢查拖曳的資料是否包含 string 物件。

    - 會使用<xref:System.Windows.DataObject.GetData%2A>方法來解壓縮字串資料 (如果有的話)。

    - 會使用<xref:System.Windows.Media.Brush>來嘗試將字串轉換成。 <xref:System.Windows.Media.BrushConverter>

    - 如果轉換成功, 會將筆刷套用至<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse>提供 Circle 控制項 UI 的的。

    - 將<xref:System.Windows.UIElement.Drop>事件標示為已處理。 您應該將置放事件標示為已處理，讓收到此事件的其他項目知道 Circle 使用者控制項已處理過它。

3. 按 **F5** 鍵建置並執行應用程式。

4. `green` 選取<xref:System.Windows.Controls.TextBox>中的文字。

5. 將文字拖放至 Circle 控制項。 Circle 會從藍色變成綠色。

     ![將字串轉換成筆刷](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. 在中輸入`green`文字。 <xref:System.Windows.Controls.TextBox>

7. `gre` 選取<xref:System.Windows.Controls.TextBox>中的文字。

8. 將它拖放至 Circle 控制項。 請注意，游標變更以指出允許置放，但 Circle 的色彩不會變更，因為 `gre` 不是有效的色彩。

9. 從綠色 Circle 控制項拖放至藍色 Circle 控制項。 Circle 會從藍色變成綠色。 請注意, 會顯示哪一個游標, 取決<xref:System.Windows.Controls.TextBox>于或圓形是否為拖曳來源。

將屬性設定為`true`並處理已捨棄的資料, 就是讓元素成為卸載目標所需的所有專案。 <xref:System.Windows.UIElement.AllowDrop%2A> 不過, 為了提供更好的使用者體驗, 您也應該處理<xref:System.Windows.UIElement.DragEnter>、 <xref:System.Windows.UIElement.DragLeave>和<xref:System.Windows.UIElement.DragOver>事件。 在這些事件中，您可以在置放資料之前執行檢查，並將其他意見反應提供給使用者。

將資料拖曳至 Circle 使用者控制項上方時，控制項應該通知拖曳來源是否可以處理所拖曳的資料。 如果控制項不知道如何處理資料，則應該拒絕置放。 若要這樣做, 您將會<xref:System.Windows.UIElement.DragOver>處理事件, 並<xref:System.Windows.DragEventArgs.Effects%2A>設定屬性。

### <a name="to-verify-that-the-data-drop-is-allowed"></a>確認允許資料置放

1. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

2. 新增下列<xref:System.Windows.UIElement.OnDragOver%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragOver>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     此<xref:System.Windows.UIElement.OnDragOver%2A>覆寫會執行下列工作:

    - 將 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。

    - 執行在<xref:System.Windows.UIElement.OnDrop%2A>方法中執行的相同檢查, 以判斷 Circle 使用者控制項是否可以處理拖曳的資料。

    - 如果使用者控制項可以處理資料, 請將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定為<xref:System.Windows.DragDropEffects.Copy>或<xref:System.Windows.DragDropEffects.Move>。

3. 按 **F5** 鍵建置並執行應用程式。

4. `gre` 選取<xref:System.Windows.Controls.TextBox>中的文字。

5. 將文字拖曳至 Circle 控制項。 請注意，游標現在會變更以指出不允許置放，因為 `gre` 不是有效的色彩。

 您可以套用置放作業的預覽，進一步增強使用者體驗。 對於 Circle 使用者控制項, 您將會覆寫<xref:System.Windows.UIElement.OnDragEnter%2A>和<xref:System.Windows.UIElement.OnDragLeave%2A>方法。 將資料拖曳至控制項上時, 會將目前的<xref:System.Windows.Shapes.Shape.Fill%2A>背景儲存在預留位置變數中。 然後, 此字串會轉換成筆刷, 並套用<xref:System.Windows.Shapes.Ellipse>至提供圓形 UI 的。 如果將資料從圓形拖曳掉而不卸載, 則會將原始<xref:System.Windows.Shapes.Shape.Fill%2A>值重新套用至圓形。

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>預覽拖放作業的效果

1. 開啟 Circle.xaml.cs 或 Circle.xaml.vb。

2. 在 Circle 類別中, 宣告名為<xref:System.Windows.Media.Brush> `_previousFill`的私用變數, 並`null`將它初始化為。

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. 新增下列<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragEnter>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     此<xref:System.Windows.UIElement.OnDragEnter%2A>覆寫會執行下列工作:

    - 將的<xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse>屬性儲存在`_previousFill`變數中。

    - 執行在<xref:System.Windows.UIElement.OnDrop%2A>方法中執行的相同檢查, 以判斷資料是否可以轉換<xref:System.Windows.Media.Brush>成。

    - 如果資料轉換成有效<xref:System.Windows.Media.Brush>的, 則會將它套用<xref:System.Windows.Shapes.Shape.Fill%2A>至<xref:System.Windows.Shapes.Ellipse>的。

4. 新增下列<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫, 以提供<xref:System.Windows.UIElement.DragLeave>事件的類別處理。

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     此<xref:System.Windows.UIElement.OnDragLeave%2A>覆寫會執行下列工作:

    - 將儲存在`_previousFill` 變數中的套用<xref:System.Windows.Shapes.Shape.Fill%2A>到提供Circle使用者控制項之UI的。<xref:System.Windows.Shapes.Ellipse> <xref:System.Windows.Media.Brush>

5. 按 **F5** 鍵建置並執行應用程式。

6. `green` 選取<xref:System.Windows.Controls.TextBox>中的文字。

7. 將文字拖曳至 Circle 控制項上方，但不置放文字。 Circle 會從藍色變成綠色。

     ![預覽拖放作業的效果](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. 從 Circle 控制項拖離文字。 Circle 會從綠色變回藍色。

## <a name="enable-a-panel-to-receive-dropped-data"></a>啟用面板以接收已捨棄的資料

在本節中, 您會啟用裝載 Circle 使用者控制項的面板, 做為拖曳的圓形資料的放置目標。 您將會執行程式碼, 讓您可以將圓形從一個面板移到另一個面板, 或在拖放圓形時按住**Ctrl**鍵來複製 circle 控制項。

1. 開啟 MainWindow.xaml。

2. 如下列 XAML 所示, 在每個<xref:System.Windows.Controls.StackPanel>控制項中, 加入和<xref:System.Windows.UIElement.Drop>事件的<xref:System.Windows.UIElement.DragOver>處理常式。 將事件<xref:System.Windows.UIElement.DragOver> <xref:System.Windows.UIElement.Drop>處理常式`panel_Drop`命名為, 並將事件處理常式命名為。 `panel_DragOver`

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. 開啟 MainWindows.xaml.cs 或 MainWindow.xaml.vb。

4. 為<xref:System.Windows.UIElement.DragOver>事件處理常式新增下列程式碼。

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     這個<xref:System.Windows.UIElement.DragOver>事件處理常式會執行下列工作:

    - 檢查拖曳的資料是否包含<xref:System.Windows.DataObject>由 Circle 使用者控制項封裝在中, 並在<xref:System.Windows.DragDrop.DoDragDrop%2A>呼叫中傳遞的「物件」資料。

    - 如果出現「物件」資料, 則會檢查是否按下**Ctrl**鍵。

    - 如果按下**Ctrl**鍵, 則會將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定<xref:System.Windows.DragDropEffects.Copy>為。 否則, 請將<xref:System.Windows.DragEventArgs.Effects%2A>屬性設定<xref:System.Windows.DragDropEffects.Move>為。

5. 為<xref:System.Windows.UIElement.Drop>事件處理常式新增下列程式碼。

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     這個<xref:System.Windows.UIElement.Drop>事件處理常式會執行下列工作:

    - 檢查是否<xref:System.Windows.UIElement.Drop>已處理事件。 比方說, 如果在處理<xref:System.Windows.UIElement.Drop>事件的另一個圓圈上放置圓形, 您不想要包含圓形的面板也可以處理它。

    - 如果未處理  事件,則會檢查是否按下Ctrl<xref:System.Windows.UIElement.Drop>鍵。

    - 如果在  <xref:System.Windows.UIElement.Drop>發生時按下 Ctrl 鍵, 則會建立 Circle 控制項的複本, 並<xref:System.Windows.Controls.Panel.Children%2A>將它加入至的集合<xref:System.Windows.Controls.StackPanel>。

    - 如果未按下**Ctrl**鍵, 則會將圓形從<xref:System.Windows.Controls.Panel.Children%2A>其<xref:System.Windows.Controls.Panel.Children%2A>父面板集合移至其所放置的面板集合。

    - 設定屬性, 以通知方法是否已執行移動或複製作業。 <xref:System.Windows.DragDrop.DoDragDrop%2A> <xref:System.Windows.DragEventArgs.Effects%2A>

6. 按 **F5** 鍵建置並執行應用程式。

7. `green` 選取<xref:System.Windows.Controls.TextBox>中的文字。

8. 將文字拖放至 Circle 控制項。

9. 將 Circle 控制項從從左面板拖放至右面板。 會從左側面板的<xref:System.Windows.Controls.Panel.Children%2A>集合中移除圓形, 並將其新增至右側面板的 [子系] 集合。

10. 將 Circle 控制項從它所在的面板拖曳到另一個面板, 並在按下**Ctrl**鍵時放置它。 會複製圓形, 並將複本新增至<xref:System.Windows.Controls.Panel.Children%2A>接收面板的集合。

     ![拖曳 Circle 時按住 CTRL 鍵](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>另請參閱

- [拖放概觀](drag-and-drop-overview.md)
