---
title: Freezable 物件概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], description
- unfreezing Freezable objects [WPF]
- classes [WPF], Freezable
ms.assetid: 89c71692-4f43-4057-b611-67c6a8a863a2
ms.openlocfilehash: 1b0bc360c4c04457e71115dc5caf935841a2bbc1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619642"
---
# <a name="freezable-objects-overview"></a>Freezable 物件概觀
本主題說明如何有效地使用，並建立<xref:System.Windows.Freezable>提供特殊功能，可協助您改善應用程式效能的物件。 Freezable 物件的範例包括筆刷、 畫筆、 轉換、 幾何和動畫。  
  
<a name="whatisafreezable"></a>   
## <a name="what-is-a-freezable"></a>什麼是 Freezable？  
 A<xref:System.Windows.Freezable>是一種特殊類型的物件，有兩種狀態︰ 未凍結和已凍結。 當解除凍結，<xref:System.Windows.Freezable>似乎像是任何其他物件的行為。 當凍結，<xref:System.Windows.Freezable>無法再修改。  
  
 A<xref:System.Windows.Freezable>提供<xref:System.Windows.Freezable.Changed>事件以通知觀察者的物件的任何修改。 凍結<xref:System.Windows.Freezable>可以改善其效能，因為它不再需要花費資源上變更通知。 凍結<xref:System.Windows.Freezable>也可以共用多個執行緒，同時未凍結<xref:System.Windows.Freezable>無法。  
  
 雖然<xref:System.Windows.Freezable>類別有許多應用程式，最<xref:System.Windows.Freezable>中的物件[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]與相關圖形的子系統。  
  
 <xref:System.Windows.Freezable>類別可讓您更輕鬆地使用某些圖形系統物件，而且可以協助改善應用程式的效能。 繼承自的類別類型的範例<xref:System.Windows.Freezable>包括<xref:System.Windows.Media.Brush>， <xref:System.Windows.Media.Transform>，和<xref:System.Windows.Media.Geometry>類別。 因為它們包含 unmanaged 的資源，系統必須監視這些物件進行修改，且原始物件變更時，然後更新其對應的 unmanaged 的資源。 即使您不會實際修改圖形系統物件，系統仍然必須用掉一些監視物件，其資源如果您變更它。  
  
 例如，假設您建立<xref:System.Windows.Media.SolidColorBrush>筆刷，並使用它來繪製按鈕的背景。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]  
  
 轉譯按鈕時，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]圖形子系統會使用您提供給繪製的像素為單位來建立 按鈕的外觀群組的資訊。 雖然您可以使用單色筆刷來描述要繪製按鈕的方式，但您的單色筆刷實際上並不進行繪製。 圖形系統會產生按鈕的筆刷，快速、 低層級物件，而且是實際在螢幕顯示這些物件。  
  
 如果您要修改的筆刷，這些低階物件必須重新產生。 Freezable 的類別可以賦予筆刷能夠尋找其對應的產生的低層級物件，以及更新這些變更時。 筆刷啟用這項功能時，就稱為 「 凍結 」。  
  
 Freezable 的<xref:System.Windows.Freezable.Freeze%2A>方法可讓您停用此自行更新功能。 您可以使用這個方法，使筆刷變成 「 凍結 」，或設為不可修改。  
  
> [!NOTE]
>  可以凍結 Freezable 的不是每個物件。 若要避免擲回<xref:System.InvalidOperationException>，檢查 Freezable 物件的值<xref:System.Windows.Freezable.CanFreeze%2A>屬性來判斷是否可以凍結再嘗試將它凍結。  
  
 [!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
 [!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]  
  
 當您不再需要修改以 freezable 時，凍結提供效能優勢。 如果您要凍結的筆刷，在此範例中，圖形系統將不再需要監視有變更。 圖形系統也可以讓其他最佳化，因為它知道筆刷並不會變更。  
  
> [!NOTE]
>  為了方便起見，除非您明確地凍結，保持未凍結 freezable 物件。  
  
<a name="frozenfreezables"></a>   
## <a name="using-freezables"></a>使用 Freezable  
 使用解除凍結 freezable 就像是使用任何其他類型的物件。 在下列範例中，色彩<xref:System.Windows.Media.SolidColorBrush>已從黃色變成紅色之後它用來繪製按鈕的背景。 圖形系統會在幕後自動變更按鈕從黃色到紅色下次重新整理畫面。  
  
 [!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
 [!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]  
  
### <a name="freezing-a-freezable"></a>凍結的 Freezable  
 若要讓<xref:System.Windows.Freezable>不可呼叫其<xref:System.Windows.Freezable.Freeze%2A>方法。 當您凍結物件，包含 freezable 物件時，這些物件也會凍結。 例如，如果您凍結<xref:System.Windows.Media.PathGeometry>，會太凍結數據和它所包含的區段。  
  
 Freezable**無法**凍結如果下列任一項成立：  
  
- 它具有動畫，或資料繫結屬性。  
  
- 它的動態資源所設定的屬性。 (請參閱[XAML 資源](xaml-resources.md)的動態資源的詳細資訊。)  
  
- 它包含<xref:System.Windows.Freezable>無法凍結的子物件。  
  
 如果這些條件都為 false，而且您不想要修改<xref:System.Windows.Freezable>，則您應該凍結它獲得稍早所述的效能優勢。  
  
 一旦您呼叫以 freezable 的<xref:System.Windows.Freezable.Freeze%2A>方法中，您可以不會再進行修改。 嘗試修改凍結物件原因<xref:System.InvalidOperationException>擲回。 下列程式碼擲回例外狀況，因為我們嘗試修改後已凍結的筆刷。  
  
 [!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
 [!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]  
  
 若要避免擲回這個例外狀況，您可以使用<xref:System.Windows.Freezable.IsFrozen%2A>方法，以判斷是否<xref:System.Windows.Freezable>已凍結。  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 在上述程式碼範例中，可修改複本已凍結的物件使用的<xref:System.Windows.Freezable.Clone%2A>方法。 下節會討論更多詳細資料複製。  
  
 **附註**因為已凍結 freezable 無法變成動畫，動畫系統會自動建立的可修改複製品凍結<xref:System.Windows.Freezable>當您嘗試以動畫顯示物件<xref:System.Windows.Media.Animation.Storyboard>。 若要消除造成的效能負荷藉由複製，讓未凍結，如果您想要以動畫顯示它的物件。 如需使用分鏡腳本以動畫顯示的詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)。  
  
### <a name="freezing-from-markup"></a>從標記凍結  
 若要凍結<xref:System.Windows.Freezable>物件的宣告是在標記中，而您使用`PresentationOptions:Freeze`屬性。 在下列範例中，<xref:System.Windows.Media.SolidColorBrush>是宣告為頁面資源和已凍結。 它接著會用來設定按鈕的背景。  
  
 [!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]  
  
 若要使用`Freeze`屬性，您必須將對應的呈現方式選項命名空間： `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`。 `PresentationOptions` 是建議的前置詞對應此命名空間：  
  
```  
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"   
```  
  
 因為並非所有的 XAML 讀取器辨識這個屬性時，建議您改用[mc: Ignorable 屬性](mc-ignorable-attribute.md)標示`Presentation:Freeze`為 ignorable 屬性：  
  
```  
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
mc:Ignorable="PresentationOptions"  
```  
  
 如需詳細資訊，請參閱 < [mc: Ignorable 屬性](mc-ignorable-attribute.md)頁面。  
  
### <a name="unfreezing-a-freezable"></a>「 取消凍結 」 Freezable  
 一次凍結<xref:System.Windows.Freezable>永遠不會修改或解除凍結; 不過，您可以建立使用的凍結的複製品<xref:System.Windows.Freezable.Clone%2A>或<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法。  
  
 在下列範例中，設定按鈕的背景筆刷和筆刷然後已凍結。 凍結的複本組成筆刷使用<xref:System.Windows.Freezable.Clone%2A>方法。 會修改複製品，並將它用來從黃色的按鈕的背景變更為紅色。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
> [!NOTE]
>  不論使用何種複製方法，動畫會永遠不會複製到新<xref:System.Windows.Freezable>。  
  
 <xref:System.Windows.Freezable.Clone%2A>和<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法會產生 freezable 的深層複本。 如果 freezable 包含其他凍結 freezable 物件，它們也會複製，而且所做的修改。 例如，如果您複製凍結<xref:System.Windows.Media.PathGeometry>進行修改，數據和它所包含的區段也複製，並進行修改。  
  
<a name="createyourownfreezableclass"></a>   
## <a name="creating-your-own-freezable-class"></a>建立您自己的 Freezable 類別  
 類別衍生自<xref:System.Windows.Freezable>獲得下列功能。  
  
- 特殊的狀態： 唯讀 （凍結） 和可寫入的狀態。  
  
- 執行緒安全： 凍結<xref:System.Windows.Freezable>可以跨執行緒共用。  
  
- 詳細的變更通知：不同於其他<xref:System.Windows.DependencyObject>s，Freezable 物件變更通知時提供子屬性值變更。  
  
- 輕鬆複製： Freezable 的類別已實作數種方法，產生深層複製品。  
  
 A<xref:System.Windows.Freezable>是一種<xref:System.Windows.DependencyObject>，並因此會使用相依性屬性系統。 您的類別屬性不必是相依性屬性，但使用相依性屬性，則會減少您必須撰寫，因為程式碼數量<xref:System.Windows.Freezable>類別的設計在心的相依性屬性。 如需有關相依性屬性系統的詳細資訊，請參閱[相依性屬性概觀](dependency-properties-overview.md)。  
  
 每隔<xref:System.Windows.Freezable>子類別必須覆寫<xref:System.Windows.Freezable.CreateInstanceCore%2A>方法。 如果您的類別會使用相依性屬性的所有資料，您就完成。  
  
 如果您的類別包含非相依性屬性資料成員，您也必須覆寫下列方法：  
  
- <xref:System.Windows.Freezable.CloneCore%2A>  
  
- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>  
  
- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>  
  
- <xref:System.Windows.Freezable.FreezeCore%2A>  
  
 您也必須遵守下列規則來存取和寫入資料成員不是相依性屬性：  
  
- 在任何開頭[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]它會讀取非相依性屬性資料成員，請呼叫<xref:System.Windows.Freezable.ReadPreamble%2A>方法。  
  
- 將寫入非相依性屬性資料成員的任何 API 開頭呼叫<xref:System.Windows.Freezable.WritePreamble%2A>方法。 (一旦您呼叫了<xref:System.Windows.Freezable.WritePreamble%2A>中[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]，您不需要進行額外的呼叫<xref:System.Windows.Freezable.ReadPreamble%2A>如果您也可以讀取非相依性屬性資料成員。)  
  
- 呼叫<xref:System.Windows.Freezable.WritePostscript%2A>方法，然後再結束寫入非相依性屬性資料成員的方法。  
  
 如果您的類別會包含非相依性屬性資料成員，則<xref:System.Windows.DependencyObject>物件，您還必須呼叫<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>方法每次您變更其中一個其值，即使您正在設定之成員`null`。  
  
> [!NOTE]
>  它是非常重要的是，您會開始每個<xref:System.Windows.Freezable>您覆寫基底實作呼叫的方法。  
  
 如需自訂的範例<xref:System.Windows.Freezable>類別，請參閱[自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- [自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
