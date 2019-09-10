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
ms.openlocfilehash: 854565e28e646ef57658e2bfdb7326d8453448d2
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856079"
---
# <a name="freezable-objects-overview"></a>Freezable 物件概觀

本主題描述如何有效地使用和建立<xref:System.Windows.Freezable>物件，以提供可協助改善應用程式效能的特殊功能。 凍結物件的範例包括筆刷、畫筆、轉換、幾何和動畫。

<a name="whatisafreezable"></a>

## <a name="what-is-a-freezable"></a>什麼是可凍結的？

<xref:System.Windows.Freezable>是特殊類型的物件, 有兩種狀態: [未凍結] 和 [已凍結]。 當未凍結時<xref:System.Windows.Freezable> ，的行為就像任何其他物件一樣。 當凍結時， <xref:System.Windows.Freezable>就無法再修改。

<xref:System.Windows.Freezable> 會<xref:System.Windows.Freezable.Changed>提供事件，以通知觀察者對物件的任何修改。 <xref:System.Windows.Freezable>凍結可以改善其效能，因為它不再需要花費資源來變更通知。 凍結<xref:System.Windows.Freezable>也可以線上程之間共用，而無法凍結<xref:System.Windows.Freezable> 。

雖然類別有許多應用程式，但<xref:System.Windows.Freezable>中[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]的大部分物件都與圖形子系統相關。 <xref:System.Windows.Freezable>

<xref:System.Windows.Freezable>類別可讓您更輕鬆地使用特定圖形系統物件，並有助於改善應用程式效能。 繼承自<xref:System.Windows.Freezable>的類型範例<xref:System.Windows.Media.Brush>包括、 <xref:System.Windows.Media.Transform>和<xref:System.Windows.Media.Geometry>類別。 因為它們包含非受控資源，所以系統必須監視這些物件以進行修改，然後在原始物件變更時，更新其對應的非受控資源。 即使您實際上不修改圖形系統物件，系統仍然必須花一些資源來監視物件，以防您進行變更。

例如，假設您建立<xref:System.Windows.Media.SolidColorBrush>筆刷，並用它來繪製按鈕的背景。

[!code-csharp[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart1)]
[!code-vb[freezablesample_procedural#FrozenExamplePart1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart1)]

當按鈕呈現時， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]圖形子系統會使用您所提供的資訊來繪製一組圖元，以建立按鈕的外觀。 雖然您使用純色筆刷來描述應該如何繪製按鈕，但是純色筆刷實際上並不會進行繪製。 圖形系統會針對按鈕和筆刷產生快速、低層級的物件，而這就是實際出現在螢幕上的物件。

如果您要修改筆刷，則必須重新產生那些低層級的物件。 可凍結的類別可讓筆刷能夠尋找其對應產生的低層級物件，並在變更時加以更新。 啟用這種功能時，筆刷就稱為「解凍」。

可凍結的<xref:System.Windows.Freezable.Freeze%2A>方法可讓您停用此自行更新的功能。 您可以使用這個方法，讓筆刷變成「凍結」或無法修改。

> [!NOTE]
> 並非每個可凍結的物件都可以凍結。 若要避免<xref:System.InvalidOperationException>擲回，請檢查可凍結<xref:System.Windows.Freezable.CanFreeze%2A>物件之屬性的值，以判斷是否可以凍結它，然後再嘗試凍結它。

[!code-csharp[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#frozenexamplepart2)]
[!code-vb[freezablesample_procedural#FrozenExamplePart2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#frozenexamplepart2)]

當您不再需要修改可凍結的時，凍結它可提供效能優勢。 如果您在此範例中凍結筆刷，圖形系統就不再需要監視它是否有變更。 圖形系統也可以進行其他優化，因為它知道筆刷不會變更。

> [!NOTE]
> 為了方便起見，除非您明確凍結，否則可凍結的物件會保持未凍結。

<a name="frozenfreezables"></a>

## <a name="using-freezables"></a>使用 Freezable

使用未凍結的可凍結，就像使用任何其他類型的物件。 在下列範例中，的色彩<xref:System.Windows.Media.SolidColorBrush>在用來繪製按鈕的背景之後，會從黃色變更為紅色。 圖形系統會在幕後運作，以在下一次重新整理螢幕時，自動將按鈕從黃色變更為紅色。

[!code-csharp[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#unfrozenexampleshort)]
[!code-vb[freezablesample_procedural#UnFrozenExampleShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#unfrozenexampleshort)]

### <a name="freezing-a-freezable"></a>凍結凍結的

若要使<xref:System.Windows.Freezable>無法修改，請呼叫<xref:System.Windows.Freezable.Freeze%2A>其方法。 當您凍結包含可凍結物件的物件時，也會凍結那些物件。 例如，如果您凍結<xref:System.Windows.Media.PathGeometry>，它所包含的圖形和區段也會凍結。

如果下列任一條件成立，就**無法**凍結可凍結的：

- 它具有動畫或資料系結屬性。

- 它具有動態資源所設定的屬性。 （如需動態資源的詳細資訊，請參閱[XAML 資源](xaml-resources.md)）。

- 它包含<xref:System.Windows.Freezable>無法凍結的子物件。

如果這些條件為 false，而且您不打算修改<xref:System.Windows.Freezable>，則您應該凍結它以取得先前所述的效能優勢。

一旦呼叫可凍結的<xref:System.Windows.Freezable.Freeze%2A>方法之後，就無法再修改它。 嘗試修改凍結的物件會導致<xref:System.InvalidOperationException>擲回。 下列程式碼會擲回例外狀況，因為我們嘗試在凍結之後修改筆刷。

[!code-csharp[freezablesample_procedural#ExceptionExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#exceptionexample)]
[!code-vb[freezablesample_procedural#ExceptionExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#exceptionexample)]

若要避免擲回這個例外狀況，您<xref:System.Windows.Freezable.IsFrozen%2A>可以使用方法來判斷<xref:System.Windows.Freezable>是否已凍結。

[!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
[!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]

在上述程式碼範例中，會使用<xref:System.Windows.Freezable.Clone%2A>方法，以已凍結的物件製作可修改的複本。 下一節會更詳細地討論複製。

> [!NOTE]
> 由於凍結的可凍結無法繪製動畫，因此當您嘗試以動畫顯示<xref:System.Windows.Freezable> <xref:System.Windows.Media.Animation.Storyboard>時，動畫系統會自動建立凍結物件的可修改複本。 若要消除複製所造成的效能額外負荷，如果您想要以動畫顯示物件，請將它保留為未凍結。 如需使用分鏡腳本製作動畫的詳細資訊，請參閱分鏡腳本[總覽](../graphics-multimedia/storyboards-overview.md)。

### <a name="freezing-from-markup"></a>從標記凍結

若要凍結<xref:System.Windows.Freezable>標記中宣告的物件，您可以`PresentationOptions:Freeze`使用屬性。 在下列範例中， <xref:System.Windows.Media.SolidColorBrush>會宣告為頁面資源並凍結。 然後，它會用來設定按鈕的背景。

[!code-xaml[FreezableSample#FreezeFromMarkupWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FreezableSample/CS/FreezeFromMarkupExample.xaml#freezefrommarkupwholepage)]

若要使用`Freeze`屬性，您必須對應至展示選項命名空間： `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options`。 `PresentationOptions`是對應此命名空間的建議前置詞：

```
xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"
```

由於並非所有的 XAML 讀取器都會辨識此屬性，因此建議您使用[mc：可忽略的屬性](mc-ignorable-attribute.md)，將`Presentation:Freeze`屬性標記為可忽略：

```
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="PresentationOptions"
```

如需詳細資訊，請參閱[mc：可忽略屬性](mc-ignorable-attribute.md)頁面。

### <a name="unfreezing-a-freezable"></a>"解除凍結" 是一個凍結的

凍結之後，永遠<xref:System.Windows.Freezable>無法修改或解除凍結，不過，您可以<xref:System.Windows.Freezable.Clone%2A>使用或<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法來建立未凍結的複製。

在下列範例中，按鈕的背景是以筆刷設定的，該筆刷會被凍結。 未凍結的複本是由使用<xref:System.Windows.Freezable.Clone%2A>方法的筆刷所組成。 複製已修改，並用於將按鈕的背景從黃色變更為紅色。

[!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
[!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]

> [!NOTE]
> 不論您使用哪一種複製方法，動畫永遠不會複製到<xref:System.Windows.Freezable>新的。

<xref:System.Windows.Freezable.Clone%2A> 和<xref:System.Windows.Freezable.CloneCurrentValue%2A>方法會產生能凍結的深層複本。 如果可凍結的包含其他已凍結的無法凍結物件，它們也會進行複製並加以修改。 例如，如果您複製凍結<xref:System.Windows.Media.PathGeometry> ，使其成為可修改的，則它所包含的圖形和區段也會一併複製並成為可修改的。

<a name="createyourownfreezableclass"></a>

## <a name="creating-your-own-freezable-class"></a>建立您自己的無法凍結類別

衍生自<xref:System.Windows.Freezable>的類別會取得下列功能。

- 特殊狀態：唯讀（凍結）和可寫入的狀態。

- 執行緒安全：凍結<xref:System.Windows.Freezable>可以線上程之間共用。

- 詳細的變更通知：不同于<xref:System.Windows.DependencyObject>其他，當子屬性值變更時，可凍結的物件會提供變更通知。

- 輕鬆複製：可凍結的類別已經執行數個可產生深層複製的方法。

<xref:System.Windows.Freezable>是的<xref:System.Windows.DependencyObject>類型，因此會使用相依性屬性系統。 您的<xref:System.Windows.Freezable>類別屬性不一定要是相依性屬性，但使用相依性屬性將會減少您必須撰寫的程式碼數量，因為類別是設計成考慮相依性屬性。 如需相依性屬性系統的詳細資訊，請參閱相依性[屬性總覽](dependency-properties-overview.md)。

每<xref:System.Windows.Freezable>個子類別都<xref:System.Windows.Freezable.CreateInstanceCore%2A>必須覆寫方法。 如果您的類別使用相依性屬性來取得其所有資料，您就已完成。

如果您的類別包含非相依性屬性資料成員，您也必須覆寫下列方法：

- <xref:System.Windows.Freezable.CloneCore%2A>

- <xref:System.Windows.Freezable.CloneCurrentValueCore%2A>

- <xref:System.Windows.Freezable.GetAsFrozenCore%2A>

- <xref:System.Windows.Freezable.GetCurrentValueAsFrozenCore%2A>

- <xref:System.Windows.Freezable.FreezeCore%2A>

您也必須觀察下列用來存取和寫入非相依性屬性之資料成員的規則：

- 在讀取非相依性屬性資料成員的任何 API 開頭，呼叫<xref:System.Windows.Freezable.ReadPreamble%2A>方法。

- 在寫入非相依性屬性資料成員的任何 API 開始時，呼叫<xref:System.Windows.Freezable.WritePreamble%2A>方法。 （在 API 中呼叫<xref:System.Windows.Freezable.WritePreamble%2A>之後， <xref:System.Windows.Freezable.ReadPreamble%2A>如果您也讀取非相依性屬性資料成員，則不需要對進行額外的呼叫）。

- 先呼叫<xref:System.Windows.Freezable.WritePostscript%2A>方法，再結束寫入非相依性屬性資料成員的方法。

如果您的類別包含屬於<xref:System.Windows.DependencyObject>物件的非相依性屬性資料成員，則您也必須在每次變更其中一個值時<xref:System.Windows.Freezable.OnFreezablePropertyChanged%2A>呼叫方法，即使您要將成員設定為`null`也一樣。

> [!NOTE]
> 請務必使用基底實作為呼叫<xref:System.Windows.Freezable>來開始覆寫的每個方法。

如需自訂<xref:System.Windows.Freezable>類別的範例，請參閱[自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Freezable>
- [自訂動畫範例](https://go.microsoft.com/fwlink/?LinkID=159981)
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
