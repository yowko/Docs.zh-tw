---
title: "Freezable 物件概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "類別, Freezable"
  - "Freezable 物件, description"
  - "解除凍結 Freezable 物件"
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 30
---
# Freezable 物件概觀
本主題描述如何有效率地使用並建立 <xref:System.Windows.Freezable> 物件，以提供可以協助改善應用程式效能的特定功能。  Freezable 物件的範例包含筆刷、畫筆、轉換、幾何和動畫。  
  
 此主題包括下列章節：  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="whatisafreezable"></a>   
## 什麼是 Freezable  
 <xref:System.Windows.Freezable> 是具有下列兩種狀態的特殊物件型別：未凍結和凍結。  未凍結時，<xref:System.Windows.Freezable> 的行為就和其他任何物件一樣。  而凍結時，則無法再修改 <xref:System.Windows.Freezable>。  
  
 <xref:System.Windows.Freezable> 提供 <xref:System.Windows.Freezable.Changed> 事件，以在發生任何物件修改時通知觀察器。  凍結 <xref:System.Windows.Freezable> 之後，因為不再需要花費資源在變更告知上，所以可以改善效能。  凍結的 <xref:System.Windows.Freezable> 物件也可以供多個執行緒共用，而未凍結的 <xref:System.Windows.Freezable> 則不可以。  
  
 雖然 <xref:System.Windows.Freezable> 類別具有許多應用程式，但是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的大部分 <xref:System.Windows.Freezable> 物件都是與圖形子系統相關。  
  
 <xref:System.Windows.Freezable> 類別可以簡化特定圖形系統物件的使用，而且可以協助改善應用程式效能。  繼承自 <xref:System.Windows.Freezable> 的型別範例包含 <xref:System.Windows.Media.Brush>、<xref:System.Windows.Media.Transform> 和 <xref:System.Windows.Media.Geometry> 類別。  因為它們包含 Unmanaged 資源，所以系統必須監視這些物件是否發生修改，然後在原始物件變更時更新這些物件的對應 Unmanaged 資源。  即使實際上未修改圖形系統物件，但系統仍然必須用掉它的一些資源來監視物件，以免您真的進行了變更。  
  
 例如，假設您建立 <xref:System.Windows.Media.SolidColorBrush> 筆刷，並使用該筆刷來繪製按鈕的背景。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 當呈現按鈕時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 圖形子系統會使用您所提供的資訊來繪製像素群組，以建立按鈕的外觀。  雖然使用純色筆刷來描述應該繪製按鈕的方式，但是純色筆刷並未實際進行繪製。  圖形系統會針對按鈕和筆刷產生快速且低階的物件，而這些就是實際顯示在螢幕上的物件。  
  
 如果要修改筆刷，則必須重新產生那些低階物件。  Freezable 類別讓筆刷可以找到與它對應的已產生低階物件，並在筆刷變更時更新這些物件。  啟用這個功能時，筆刷就稱為「未凍結」。  
  
 Freezable 的 <xref:System.Windows.Freezable.Freeze%2A> 方法可讓您停用這個自我更新功能。  您可以使用這個方法，讓筆刷變成「已凍結」或不可以修改的。  
  
> [!NOTE]
>  並非所有 Freezable 物件都可以進行凍結。  為了避免擲回 <xref:System.InvalidOperationException>，請在嘗試凍結之前，先檢查 Freezable 物件的 <xref:System.Windows.Freezable.CanFreeze%2A> 屬性值，判斷是否可以進行凍結。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 當您不再需要修改 Freezable 時，將它凍結可提高效能。  如果要凍結這個範例中的筆刷，圖形系統就不再需要監視筆刷是否變更。  因為圖形系統知道筆刷不會變更，所以圖形系統也可以進行其他最佳化。  
  
> [!NOTE]
>  為了方便使用，Freezable 物件在明確凍結之前都會保留未凍結狀態。  
  
<a name="frozenfreezables"></a>   
## 使用 Freezable  
 使用未凍結的 Freezable 就和使用其他物件型別一樣。  在下列範例中，使用 <xref:System.Windows.Media.SolidColorBrush> 繪製按鈕的背景之後，它的顏色會從黃色變更為紅色。  圖形系統會在場景後面作業，以在下次重新整理螢幕時自動將按鈕的顏色從黃色變更為紅色。  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### 凍結 Freezable  
 若要讓 <xref:System.Windows.Freezable> 變為不可修改，請呼叫它的 <xref:System.Windows.Freezable.Freeze%2A> 方法。  當您凍結的物件內含 Freezable 物件時，那些物件也會一併凍結。  例如，如果凍結 <xref:System.Windows.Media.PathGeometry>，則也會一併凍結它所含的圖形和區段。  
  
 如果符合下列任一項，就「不可以」凍結 Freezable 物件：  
  
-   具有顯示為動畫或資料繫結屬性。  
  
-   具有動態資源設定的屬性   \(如需動態資源的詳細資訊，請參閱[XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)\)。  
  
-   包含無法凍結的 <xref:System.Windows.Freezable> 子物件。  
  
 如果不符合上述條件，而且不想要修改 <xref:System.Windows.Freezable>，則應該考慮將之凍結，如前所述來提升效能。  
  
 呼叫 Freezable 的 <xref:System.Windows.Freezable.Freeze%2A> 方法之後，就無法再修改 Freezable。  如果嘗試修改已凍結的物件，則會擲回 <xref:System.InvalidOperationException>。  在下列程式碼中，因為我們會在凍結筆刷之後嘗試修改該筆刷，所以會擲回例外狀況。  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 為了避免擲回這個例外狀況，可以使用 <xref:System.Windows.Freezable.IsFrozen%2A> 方法，判斷 <xref:System.Windows.Freezable> 是否已凍結。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 在上述程式碼範例中，使用 <xref:System.Windows.Freezable.Clone%2A> 方法建立了凍結物件的可修改複本。  下一節會詳細討論複製 \(Clone\)。  
  
 **注意**：因為已凍結的 Freezable 無法建立動畫，所以在您嘗試使用 <xref:System.Windows.Media.Animation.Storyboard> 建立已凍結 <xref:System.Windows.Freezable> 物件的動畫時，動畫系統會自動建立這些凍結物件的可修改複製品 \(Clone\)。  如果想要建立物件的動畫，則請將物件保留為未凍結狀態，以去除複製所造成的效能負荷。  如需使用腳本建立動畫的詳細資訊，請參閱[腳本概觀](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)。  
  
### 透過標記進行凍結  
 若要凍結以標記宣告的 <xref:System.Windows.Freezable> 物件，請使用 `PresentationOptions:Freeze` 屬性。  在下列範例中，<xref:System.Windows.Media.SolidColorBrush> 宣告為頁面資源，而且已凍結。  接著會使用它來設定按鈕的背景。  
  
 [!code-xml[FreezableSample#FreezeFromMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 若要使用 `Freeze` 屬性，則必須對應至呈現選項命名空間：`http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`。  `PresentationOptions` 是對應這個命名空間的建議前置字元：  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 因為並非所有 XAML 讀取器 \(Reader\) 都可以辨識這個屬性，所以建議您使用 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)將 `Presentation:Freeze` 屬性標示為可忽略：  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 如需詳細資訊，請參閱 [mc:Ignorable 屬性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)網頁。  
  
### 解除凍結 Freezable  
 一旦凍結之後，就不可以再修改或解除凍結 <xref:System.Windows.Freezable>，但您可以使用 <xref:System.Windows.Freezable.Clone%2A> 或 <xref:System.Windows.Freezable.CloneCurrentValue%2A> 方法建立未凍結的複製品。  
  
 在下列範例中，使用筆刷設定按鈕的背景，隨後凍結該筆刷。  然後使用 <xref:System.Windows.Freezable.Clone%2A> 方法建立筆刷的未凍結複本。  接著修改該複製品，用來將按鈕的背景從黃色變更為紅色。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  不論使用哪種複製方法，都絕不會將動畫複製至新的 <xref:System.Windows.Freezable>。  
  
 <xref:System.Windows.Freezable.Clone%2A> 和 <xref:System.Windows.Freezable.CloneCurrentValue%2A> 方法都會產生 Freezable 的深層複本 \(Deep Copy\)。  如果 Freezable 包含其他凍結的 Freezable 物件，則也會一併複製它們，並將它們製作為可修改的。  例如，如果複製凍結的 <xref:System.Windows.Media.PathGeometry> 以將它製作為可修改的，則也會一併複製它所含的圖形和區段，並將它們製作為可修改的。  
  
<a name="createyourownfreezableclass"></a>   
## 建立您自己的 Freezable 類別  
 衍生自 <xref:System.Windows.Freezable> 的類別會獲得下列功能。  
  
-   特殊狀態：唯讀 \(凍結\) 和可寫入狀態。  
  
-   執行緒安全：凍結的 <xref:System.Windows.Freezable> 可以供多個執行緒共用。  
  
-   詳細變更告知：不同於其他 <xref:System.Windows.DependencyObject>，Freezable 物件會在子屬性值變更時提供變更告知。  
  
-   容易複製：Freezable 類別已實作數種可產生深層複製品的方法。  
  
 <xref:System.Windows.Freezable> 的型別為 <xref:System.Windows.DependencyObject>，因此使用相依性屬性系統。  您的類別屬性並不需要是相依性屬性，但因為 <xref:System.Windows.Freezable> 類別的本質是以相依性屬性來設計的，所以使用相依性屬性可以減少需要撰寫的程式碼數量。  如需相依性屬性系統的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。  
  
 每個 <xref:System.Windows.Freezable> 子類別都會覆寫 <xref:System.Windows.Freezable.CreateInstanceCore%2A> 方法。  如果類別的所有資料都使用相依性屬性，則作業已完成。  
  
 如果類別包含非相依性屬性資料成員，則也必須覆寫下列方法：  
  
-   <xref:System.Windows.Freezable.CloneCore%2A>  
  
-   <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
-   <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
-   <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 您也必須觀察下列規則，以存取和寫入至非相依性屬性的資料成員：  
  
-   在任何讀取非相依性屬性資料成員之 [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] 的開頭，呼叫 <xref:System.Windows.Freezable.ReadPreamble%2A> 方法。  
  
-   在任何寫入非相依性屬性資料成員之 API 的開頭，呼叫 <xref:System.Windows.Freezable.WritePreamble%2A> 方法   \(在 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 中呼叫 <xref:System.Windows.Freezable.WritePreamble%2A> 之後，如果也要讀取非相依性屬性資料成員，則不需要額外呼叫 <xref:System.Windows.Freezable.ReadPreamble%2A>\)。  
  
-   在結束寫入至非相依性屬性資料成員的方法之前，呼叫 <xref:System.Windows.Freezable.WritePostscript%2A> 方法。  
  
 如果類別包含為 <xref:System.Windows.DependencyObject> 物件的非相依性屬性資料成員，則每次變更它們的值時 \(即使是將成員設定為 `null`\)，也必須呼叫 <xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A> 方法。  
  
> [!NOTE]
>  十分重要的是透過呼叫基本實作開始每個覆寫的 <xref:System.Windows.Freezable> 方法。  
  
 如需自訂 <xref:System.Windows.Freezable> 類別的範例，請參閱[自訂動畫範例](http://go.microsoft.com/fwlink/?LinkID=159981) \(英文\)。  
  
## 請參閱  
 <xref:System.Windows.Freezable>   
 [自訂動畫範例](http://go.microsoft.com/fwlink/?LinkID=159981)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)