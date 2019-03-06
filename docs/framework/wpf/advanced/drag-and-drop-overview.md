---
title: 拖放概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], implementing
- drag sources [WPF], drag-and-drop
- data transfer [WPF], drag-and-drop
- drag-and-drop [WPF], about
- drag-and-drop [WPF], events
- drop targets [WPF], drag-and-drop
ms.assetid: 1a5b27b0-0ac5-4cdf-86c0-86ac0271fa64
ms.openlocfilehash: 67c332b4fd4d2937f3a455353f3a5353dde10ef5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356477"
---
# <a name="drag-and-drop-overview"></a>拖放概觀
本主題提供 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 應用程式中的拖放功能支援概觀。 拖放功能一般是指資料傳送的方法，這種方法需要使用滑鼠 (或其他一些指標裝置) 選取一或多個物件，將這些物件拖曳到 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中一些想要的置放目標上，然後置放這些物件。  
  
  
<a name="Drag_and_Drop_Support"></a>   
## <a name="drag-and-drop-support-in-wpf"></a>WPF 中的拖放功能支援  
 拖放作業通常涉及兩方：一方是拖曳之物件所源自的拖曳來源，另一方是接收置放之物件的置放目標。  拖曳來源和置放目標可能是相同應用程式或不同應用程式中的 UI 項目。  
  
 您可以透過拖放功能，操作任意類型和數目的物件。 例如，檔案、資料夾和選取的內容是一些可透過拖放作業來操作的較常見物件。  
  
 拖放作業期間所執行的特定動作是針對應用程式的動作，而且這些動作通常會取決於內容。  例如，將選取的檔案從一個資料夾拖曳到同一個存放裝置上的另一個資料夾預設會移動檔案，而將檔案從 [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)] 共用拖曳到本機資料夾複本預設會複製檔案。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 所提供的拖放功能是為了提高彈性和可自訂性所設計，以便支援各種拖放案例。  拖放功能支援在單一應用程式中，或在不同的應用程式之間操作物件； 拖曳放之間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]也完全支援應用程式和其他 Windows 應用程式。  
  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，任何 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 都可以參與拖放。 拖放作業所需的事件和方法會在 <xref:System.Windows.DragDrop> 類別中定義。 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 類別包含 <xref:System.Windows.DragDrop> 附加事件的別名，因此當繼承 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 做為基底項目時，便會在類別成員清單中顯示這些事件。 附加至這些事件的事件處理常式會附加至基礎 <xref:System.Windows.DragDrop> 附加事件，並接收相同的事件資料執行個體。 如需詳細資訊，請參閱 <xref:System.Windows.UIElement.Drop?displayProperty=nameWithType> 事件。  
  
> [!IMPORTANT]
>  您無法在網際網路區域中執行 OLE 拖放作業。  
  
<a name="Data_Transfer"></a>   
## <a name="data-transfer"></a>資料傳輸  
 拖放功能是範圍較廣之資料傳輸的一部分。 資料傳輸包括拖放以及複製和貼上作業。 拖放作業類似複製和貼上或剪下和貼上作業，後者使用系統剪貼簿，將資料從某個物件或應用程式傳送到另一個物件或應用程式。 這兩種作業類型都需要：  
  
-   提供資料來源物件。  
  
-   暫時儲存所傳送之資料的方式。  
  
-   接收資料的目標物件。  
  
 在複製和貼上作業中，會使用系統剪貼簿來暫時儲存所傳送的資料；在拖放作業中，會使用 <xref:System.Windows.DataObject> 來儲存資料。 資料物件在概念上是由一或多組 <xref:System.Object> (其中包含實際資料) 和對應的資料格式識別項所組成。  
  
 拖曳來源會呼叫靜態 <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> 方法，並將所傳送的資料傳遞給該方法，來啟始拖放作業。 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法會視需要自動將資料包裝在 <xref:System.Windows.DataObject> 中。 為了進一步控制資料格式，您可以將資料包裝在 <xref:System.Windows.DataObject> 中，再傳遞給 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法。 置放目標負責從 <xref:System.Windows.DataObject> 擷取資料。 如需使用資料物件的詳細資訊，請參閱[資料和資料物件](data-and-data-objects.md)。  
  
 拖放作業的來源和目標是 UI 項目；不過，實際上要傳送的資料通常並沒有視覺表示。 您可以撰寫程式碼，提供拖曳之資料的視覺表示，例如在 Windows 檔案總管中拖曳檔案時所發生的視覺表示。 根據預設，當變更游標時，系統會提供回饋給使用者，以表示這項拖放作業會對資料產生何種效果，例如是否要移動或複製資料。  
  
### <a name="drag-and-drop-effects"></a>拖放效果  
 拖放作業對傳送的資料可以有不同的效果。 例如，您可以複製或移動資料。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 定義 <xref:System.Windows.DragDropEffects> 列舉，可供您用來指定拖放作業的效果。 在拖曳來源中，您可以指定來源將在 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法中允許的效果。 在置放目標中，您可以指定目標預期用於 <xref:System.Windows.DragEventArgs> 類別之 <xref:System.Windows.DragEventArgs.Effects%2A> 屬性的效果。 當置放目標在 <xref:System.Windows.DragDrop.DragOver> 事件中指定其預期效果時，該資訊會在 <xref:System.Windows.DragDrop.GiveFeedback> 事件中傳回拖曳來源。 拖曳來源會使用這項資訊，來通知使用者置放目標預期用於資料的效果。 置放資料之後，置放目標會在 <xref:System.Windows.DragDrop.Drop> 事件中指定其實際效果。 該資訊會當做 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法的傳回值傳回拖曳來源。 如果置放目標傳回的效果不在 `allowedEffects` 的拖曳來源清單中，則會取消拖放作業，而不傳送任何資料。  
  
 請務必記住，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，<xref:System.Windows.DragDropEffects> 值只能用來提供拖曳來源和置放目標之間有關拖放作業效果的通訊。 拖放作業的實際效果取決於您在應用程式中撰寫的適當程式碼。  
  
 例如，置放目標可能指定資料資料的效果是移動資料。 不過，若要移動資料，該資料必須同時加入目標項目並從來源項目中移除。 來源項目可能指定允許移動資料，但如果您未提供將資料從來源項目中移除的程式碼，最後結果會是複製資料，而不是移動資料。  
  
<a name="Drag_and_Drop_Events"></a>   
## <a name="drag-and-drop-events"></a>拖放事件  
 拖放作業支援事件驅動模型。  拖曳來源和置放目標都是使用一組標準的事件來處理拖放作業。  下表摘要說明這些標準的拖放事件。 這些事件是 <xref:System.Windows.DragDrop> 類別上的附加事件。 如需附加事件的詳細資訊，請參閱[附加事件概觀](attached-events-overview.md)。  
  
### <a name="drag-source-events"></a>拖曳來源事件  
  
|事件|總結|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.GiveFeedback>|這個事件會在拖放作業期間持續發生，並可讓拖曳來源提供回饋資訊給使用者。 當變更滑鼠指標的外觀以表示置放目標所允許的效果時，通常會提供這個回饋。  這是反昇事件。|  
|<xref:System.Windows.DragDrop.QueryContinueDrag>|這個事件會在拖曳作業期間鍵盤或滑鼠按鈕狀態變更時發生，並可讓拖曳來源根據按鍵/按鈕狀態來取消拖放作業。 這是反昇事件。|  
|<xref:System.Windows.DragDrop.PreviewGiveFeedback>|
  <xref:System.Windows.DragDrop.GiveFeedback> 的通道版本。|  
|<xref:System.Windows.DragDrop.PreviewQueryContinueDrag>|
  <xref:System.Windows.DragDrop.QueryContinueDrag> 的通道版本。|  
  
### <a name="drop-target-events"></a>置放目標事件  
  
|事件|總結|  
|-----------|-------------|  
|<xref:System.Windows.DragDrop.DragEnter>|這個事件會在將物件拖曳到置放目標的界限內時發生。 這是反昇事件。|  
|<xref:System.Windows.DragDrop.DragLeave>|這個事件會在將物件拖曳出置放目標的界限時發生。  這是反昇事件。|  
|<xref:System.Windows.DragDrop.DragOver>|這個事件會在將物件拖曳 (移動) 到置放目標的界限內時持續發生。 這是反昇事件。|  
|<xref:System.Windows.DragDrop.Drop>|這個事件會在將物件置放到置放目標上時發生。  這是反昇事件。|  
|<xref:System.Windows.DragDrop.PreviewDragEnter>|
  <xref:System.Windows.DragDrop.DragEnter> 的通道版本。|  
|<xref:System.Windows.DragDrop.PreviewDragLeave>|
  <xref:System.Windows.DragDrop.DragLeave> 的通道版本。|  
|<xref:System.Windows.DragDrop.PreviewDragOver>|
  <xref:System.Windows.DragDrop.DragOver> 的通道版本。|  
|<xref:System.Windows.DragDrop.PreviewDrop>|
  <xref:System.Windows.DragDrop.Drop> 的通道版本。|  
  
 若要處理物件執行個體的拖放事件，請針對上表所列的事件加入處理常式。 若要在類別層級處理拖放事件，請覆寫對應的虛擬 On*Event 和 On\*PreviewEvent 方法。 如需詳細資訊，請參閱[控制項基底類別的路由事件類別處理](marking-routed-events-as-handled-and-class-handling.md#Class_Handling_of_Routed_Events)。  
  
<a name="Implementing_Drag_And_Drop"></a>   
## <a name="implementing-drag-and-drop"></a>實作拖放功能  
 UI 項目可以是拖曳來源和 (或) 置放目標。 若要實作基本拖放功能，您可以撰寫程式碼來啟始拖放作業並處理置放的資料。 您可以藉由處理選擇性拖放事件，來增強拖放體驗。  
  
 若要實作基本拖放功能，您將完成下列工作：  
  
-   識別將做為拖曳來源的項目。 拖曳來源可以是 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement>。  
  
-   在要啟始拖放作業的拖曳來源上建立事件處理常式。 這個事件通常是 <xref:System.Windows.UIElement.MouseMove> 事件。  
  
-   在拖曳來源事件處理常式中，呼叫 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法來啟始拖放作業。 在 <xref:System.Windows.DragDrop.DoDragDrop%2A> 呼叫中，指定拖曳來源、要傳送的資料和允許的效果。  
  
-   識別將做為置放目標的項目。 置放目標可以是 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement>。  
  
-   在置放目標上，將 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性設定為 `true`。  
  
-   在置放目標上，建立 <xref:System.Windows.DragDrop.Drop> 事件處理常式來處理置放的資料。  
  
-   在 <xref:System.Windows.DragDrop.Drop> 事件處理常式中，使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 和 <xref:System.Windows.DataObject.GetData%2A> 方法從 <xref:System.Windows.DragEventArgs> 擷取資料。  
  
-   在 <xref:System.Windows.DragDrop.Drop> 事件處理常式中，使用資料來執行所需的拖放作業。  
  
 您可以建立自訂 <xref:System.Windows.DataObject>，並處理選擇性拖曳來源和置放目標事件，來增強您的拖放功能實作，如下列工作所示：  
  
-   若要傳送自訂資料或多個資料項目，請建立 <xref:System.Windows.DataObject> 以傳遞給 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法。  
  
-   若要在拖曳期間執行其他動作，請處理置放目標上的 <xref:System.Windows.DragDrop.DragEnter>、<xref:System.Windows.DragDrop.DragOver> 和  <xref:System.Windows.DragDrop.DragLeave> 事件。  
  
-   若要變更滑鼠指標的外觀，請處理拖曳來源上的 <xref:System.Windows.DragDrop.GiveFeedback>  事件。  
  
-   若要變更拖放作業的取消方式，請處理拖曳來源上的 <xref:System.Windows.DragDrop.QueryContinueDrag> 事件。  
  
<a name="Drag_And_Drop_Example"></a>   
## <a name="drag-and-drop-example"></a>拖放功能範例  
 本節說明如何實作 <xref:System.Windows.Shapes.Ellipse> 項目的拖放功能。 <xref:System.Windows.Shapes.Ellipse> 同時為拖曳來源和置放目標。 傳送的資料是橢圓形之 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性的字串表示。 下列 XAML 顯示 <xref:System.Windows.Shapes.Ellipse> 項目及其處理的拖放相關事件。 如需如何實作拖放的完整步驟，請參閱[逐步解說：啟用拖放使用者控制項上的卸除](walkthrough-enabling-drag-and-drop-on-a-user-control.md)。  
  
 [!code-xaml[DragDropSnippets#EllipseXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#ellipsexaml)]  
  
### <a name="enabling-an-element-to-be-a-drag-source"></a>使某個項目成為拖曳來源  
 拖曳來源物件負責：  
  
-   識別何時發生拖曳。  
  
-   啟始拖放作業。  
  
-   識別要傳送的資料。  
  
-   指定傳送的資料允許的拖放作業效果。  
  
 不論允許的動作為何 (移動、複製、無)，拖曳來源也會提供回饋給使用者，並可根據其他使用者輸入 (例如在拖曳時按 ESC 鍵) 來取消拖放作業。  
  
 您的應用程式會負責判斷何時發生拖曳，然後再呼叫 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法啟始拖放作業。 一般而言，這會是在項目上按下滑鼠按鈕拖曳時所發生的 <xref:System.Windows.UIElement.MouseMove> 事件。 下列範例示範如何從 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.UIElement.MouseMove> 事件處理常式啟始拖放作業，使該項目成為拖曳來源。 傳送的資料是橢圓形之 <xref:System.Windows.Shapes.Shape.Fill%2A> 屬性的字串表示。  
  
 [!code-csharp[DragDropSnippets#DoDragDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dodragdrop)]
 [!code-vb[DragDropSnippets#DoDragDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dodragdrop)]  
  
 在 <xref:System.Windows.UIElement.MouseMove> 事件處理常式中，呼叫 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法來啟始拖放作業。 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法採用三個參數：  
  
-   `dragSource` - 所傳送之資料來源的相依性物件參考，通常是 <xref:System.Windows.UIElement.MouseMove> 事件的來源。  
  
-   `data` - 包含所傳送之資料的物件，該資料會包裝在 <xref:System.Windows.DataObject> 中。  
  
-   `allowedEffects` - <xref:System.Windows.DragDropEffects> 列舉值之一，指定允許的拖放作業效果。  
  
 所有可序列化的物件都可以 `data` 參數傳遞。 如果資料尚未包裝在 <xref:System.Windows.DataObject>  中，則會自動包裝在新的 <xref:System.Windows.DataObject> 中。 若要傳遞多個資料項目，您必須自行建立 <xref:System.Windows.DataObject>，並傳遞給 <xref:System.Windows.DragDrop.DoDragDrop%2A> 方法。 如需詳細資訊，請參閱[資料和資料物件](data-and-data-objects.md)。  
  
 `allowedEffects` 參數可用來指定拖曳來源允許置放目標對所傳送的資料執行的動作。 拖曳來源的常見值包括 <xref:System.Windows.DragDropEffects.Copy>、<xref:System.Windows.DragDropEffects.Move> 和  <xref:System.Windows.DragDropEffects.All>。  
  
> [!NOTE]
>  您也可以使用置放目標，來指定預期要回應置放資料的效果。 例如，如果置放目標無法辨識要置放的資料類型，可透過將其允許的效果設定為 <xref:System.Windows.DragDropEffects.None> 來拒絕資料。 通常會在 <xref:System.Windows.DragDrop.DragOver> 事件處理常式中執行這項作業。  
  
 拖曳來源可選擇性地處理 <xref:System.Windows.DragDrop.GiveFeedback> 和 <xref:System.Windows.DragDrop.QueryContinueDrag> 事件。 除非您將事件標記為已處理，否則這些事件會使用預設處理常式。 除非您有變更其預設行為的特定需求，否則通常會忽略這些事件。  
  
 在拖曳來源被拖曳的期間，會持續引發 <xref:System.Windows.DragDrop.GiveFeedback> 事件。 這個事件的預設處理常式會檢查拖曳來源是否在有效的置放目標上。 如果是，則會檢查允許的置放目標效果。 然後將允許的置放效果回饋給使用者。 透過將滑鼠游標變更為不置放、複製或移動游標，通常可以完成這項作業。 只有在需要使用自訂游標提供回饋給使用者時，才應該處理這個事件。 如果您處理這個事件，請務必將它標記為已處理，如此一來，預設處理常式便不會覆寫您的處理常式。  
  
 在拖曳來源被拖曳的期間，會持續引發 <xref:System.Windows.DragDrop.QueryContinueDrag> 事件。 您可以處理這個事件，根據 ESC、SHIFT、CTRL 鍵和 ALT 鍵的狀態，以及滑鼠按鈕的狀態，來決定拖放作業的結束動作。 這個事件的預設處理常式會在按下 ESC 鍵時取消拖放作業，並在放開滑鼠按鈕時置放資料。  
  
> [!CAUTION]
>  在拖放作業期間，會持續引發這些事件。 因此，您應該避免事件處理常式有需要大量資源的工作。  例如，使用快取資料指標，而不是每次引發 <xref:System.Windows.DragDrop.GiveFeedback> 事件都建立新的資料指標。  
  
### <a name="enabling-an-element-to-be-a-drop-target"></a>使某個項目成為置放目標  
 置放目標物件負責：  
  
-   指出它是有效的置放目標。  
  
-   在拖曳來源被拖曳到目標上時回應拖曳來源。  
  
-   檢查傳送的資料格式是可接收的格式。  
  
-   處理置放的資料。  
  
 若要指定某個項目做為置放目標，您可以將其 <xref:System.Windows.UIElement.AllowDrop%2A> 屬性設定為 `true`。 接著會在項目上引發置放目標事件，以便您處理這些事件。 在拖放作業期間，置放目標上會發生以下一連串事件：  
  
1.  <xref:System.Windows.DragDrop.DragEnter>  
  
2.  <xref:System.Windows.DragDrop.DragOver>  
  
3.  <xref:System.Windows.DragDrop.DragLeave> 或 <xref:System.Windows.DragDrop.Drop>  
  
 <xref:System.Windows.DragDrop.DragEnter> 事件會在將資料拖曳到置放目標的界限內時發生。 您通常會處理這個事件來預覽拖放作業的效果 (如果適用於應用程式的話)。 請勿在 <xref:System.Windows.DragDrop.DragEnter> 事件中設定 <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> 屬性，因為它會在 <xref:System.Windows.DragDrop.DragOver> 事件中遭到覆寫。  
  
 下列範例示範 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.DragDrop.DragEnter> 事件處理常式。 這個程式碼會儲存目前的 <xref:System.Windows.Shapes.Shape.Fill%2A> 筆刷，來預覽拖放作業的效果。 接著它會使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 方法來檢查是否將 <xref:System.Windows.DataObject> 拖曳到橢圓形上，該橢圓形包含可轉換成 <xref:System.Windows.Media.Brush> 的字串資料。 如果是，則會使用 <xref:System.Windows.DataObject.GetData%2A> 方法擷取資料。 接著它會轉換成 <xref:System.Windows.Media.Brush> 並套用至橢圓形。 這項變更會在 <xref:System.Windows.DragDrop.DragLeave> 事件處理常式中還原。 如果無法將資料轉換成 <xref:System.Windows.Media.Brush>，則不會執行任何動作。  
  
 [!code-csharp[DragDropSnippets#DragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragenter)]
 [!code-vb[DragDropSnippets#DragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragenter)]  
  
 
  <xref:System.Windows.DragDrop.DragOver> 事件會在將資料拖曳到置放目標上時持續發生。 這個事件會搭配拖曳來源上的 <xref:System.Windows.DragDrop.GiveFeedback> 事件。 在 <xref:System.Windows.DragDrop.DragOver> 事件處理常式中，您通常會使用 <xref:System.Windows.DataObject.GetDataPresent%2A> 和 <xref:System.Windows.DataObject.GetData%2A> 方法來檢查傳送的資料格式是否為置放目標可以處理的格式。 您也可以檢查是否按下任何輔助按鍵，這通常會指出使用者是否想要移動或複製動作。 執行這些檢查之後，您可以設定 <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> 屬性，以通知拖曳來源有關置放資料的效果。 拖曳來源會以 <xref:System.Windows.DragDrop.GiveFeedback> 事件引數接收這項資訊，並可設定適當的資料指標來提供回饋給使用者。  
  
 下列範例示範 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.DragDrop.DragOver> 事件處理常式。 這個程式碼會檢查是否要將 <xref:System.Windows.DataObject> 拖曳到橢圓形上，該橢圓形包含可轉換成 <xref:System.Windows.Media.Brush> 的字串資料。 如果是，則會將 <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Windows.DragDropEffects.Copy>。 這會向拖曳來源表示資料可以複製到橢圓形。 如果無法將資料轉換成 <xref:System.Windows.Media.Brush>，則會將 <xref:System.Windows.DragEventArgs.Effects%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.Windows.DragDropEffects.None>。 這會向拖曳來源表示橢圓形不是資料的有效置放目標。  
  
 [!code-csharp[DragDropSnippets#DragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragover)]
 [!code-vb[DragDropSnippets#DragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragover)]  
  
 
  <xref:System.Windows.DragDrop.DragLeave> 事件會在將資料拖曳出目標的界限但未置放時發生。 您可以處理這個事件，以復原您在 <xref:System.Windows.DragDrop.DragEnter> 事件處理常式中執行的任何動作。  
  
 下列範例示範 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.DragDrop.DragLeave> 事件處理常式。 這個程式碼透過將儲存的 <xref:System.Windows.Media.Brush> 套用至橢圓形，來復原在 <xref:System.Windows.DragDrop.DragEnter> 事件處理常式中執行的預覽。  
  
 [!code-csharp[DragDropSnippets#DragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#dragleave)]
 [!code-vb[DragDropSnippets#DragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#dragleave)]  
  
 
  <xref:System.Windows.DragDrop.Drop> 事件會在將資料置放到置放目標上時發生；根據預設，當放開滑鼠按鈕時，就會發生這個事件。 在 <xref:System.Windows.DragDrop.Drop> 事件處理常式中，您可以使用 <xref:System.Windows.DataObject.GetData%2A> 方法從 <xref:System.Windows.DataObject> 擷取傳送的資料，並執行應用程式所需的任何資料處理。 <xref:System.Windows.DragDrop.Drop> 事件會結束拖放作業。  
  
 下列範例示範 <xref:System.Windows.Shapes.Ellipse> 項目的 <xref:System.Windows.DragDrop.Drop> 事件處理常式。 這個程式碼會套用拖放作業的效果，類似 <xref:System.Windows.DragDrop.DragEnter> 事件處理常式中的程式碼。 它會檢查是否要將 <xref:System.Windows.DataObject> 拖曳到橢圓形上，該橢圓形包含可轉換成 <xref:System.Windows.Media.Brush> 的字串資料。 如果是，則會將 <xref:System.Windows.Media.Brush> 套用至橢圓形。 如果無法將資料轉換成 <xref:System.Windows.Media.Brush>，則不會執行任何動作。  
  
 [!code-csharp[DragDropSnippets#Drop](~/samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#drop)]
 [!code-vb[DragDropSnippets#Drop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#drop)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Clipboard>
- [逐步解說：啟用拖曳並放在使用者控制項](walkthrough-enabling-drag-and-drop-on-a-user-control.md)
- [HOW-TO 主題](drag-and-drop-how-to-topics.md)
- [拖放](drag-and-drop.md)
