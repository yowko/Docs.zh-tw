---
title: HOW TO：指定繫結來源
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], binding sources
- data binding [WPF], binding source
- binding sources [WPF]
ms.assetid: 55d47757-2648-4a52-987f-b767953f168c
ms.openlocfilehash: 8c866502300c50e00f1393b9e3fb64099f027c43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222298"
---
# <a name="how-to-specify-the-binding-source"></a>HOW TO：指定繫結來源
在資料繫結中，繫結來源物件是指您的資料取得來源物件。 本主題說明指定繫結來源的不同方式。  
  
## <a name="example"></a>範例  
 如果您將數個屬性繫結至同一個來源，要使用 `DataContext` 屬性，它是建立範圍的便利方式，在這個範圍中所有資料繫結屬性都繼承同一個來源。  
  
 下列範例會在應用程式的根元素建立資料內容。 這會使所有子元素都繼承這個資料內容。 繫結的資料來自自訂的資料類別 `NetIncome`，這個類別是直接透過對應來參考，並且具有資源索引鍵 `incomeDataSource`。  
  
 [!code-xaml[DirectionalBinding#DataContext1](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext1)]  
[!code-xaml[DirectionalBinding#DataContext2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#datacontext2)]  
  
 下列範例顯示 `NetIncome` 類別的定義。  
  
 [!code-csharp[DirectionalBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/billsdata.cs#dataobject)]
 [!code-vb[DirectionalBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DirectionalBinding/VisualBasic/NetIncome.vb#dataobject)]  
  
> [!NOTE]
>  上述範例將標記中的物件具現化，並當做資源使用。 如果您想繫結至已在程式碼中具現化的物件，必須以程式設計的方式設定 `DataContext` 屬性。 如需範例，請參閱[讓資料可於 XAML 中繫結](how-to-make-data-available-for-binding-in-xaml.md)。  
  
 或者，如果您想明確指定個別繫結的來源，則有以下選擇。 這些屬性優先於繼承的資料內容。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Data.Binding.Source%2A>|使用這個屬性將來源設定為物件的執行個體。 如果您不需要的功能建立的範圍中的數個屬性都繼承相同的資料內容，您可以使用<xref:System.Windows.Data.Binding.Source%2A>屬性而非`DataContext`屬性。 如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.Source%2A>。|  
|<xref:System.Windows.Data.Binding.RelativeSource%2A>|當您想以相對於繫結目標的位置指定來源，這十分有用。 使用這個屬性的常見案例是，當您想將元素的一個屬性繫結至同一元素的其他屬性時，或當您正在樣式或範本中定義繫結時。 如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.RelativeSource%2A>。|  
|<xref:System.Windows.Data.Binding.ElementName%2A>|指定一個字串來代表您想繫結至的元素。 當您想要繫結至應用程式中其他元素的屬性時，這十分有用。 比方說，如果您想要使用<xref:System.Windows.Controls.Slider>控制的應用程式中的另一個控制項的高度或如果您想要繫結<xref:System.Windows.Controls.ContentControl.Content%2A>的控制項<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>屬性您<xref:System.Windows.Controls.ListBox>控制項。 如需詳細資訊，請參閱<xref:System.Windows.Data.Binding.ElementName%2A>。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.FrameworkElement.DataContext%2A?displayProperty=nameWithType>
- <xref:System.Windows.FrameworkContentElement.DataContext%2A?displayProperty=nameWithType>
- [屬性值繼承](../advanced/property-value-inheritance.md)
- [資料繫結概觀](data-binding-overview.md)
- [繫結宣告概觀](binding-declarations-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
