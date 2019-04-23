---
title: HOW TO：根據繫結項目的清單產生值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: c2ec5ff26c89649294df266e790445e5aa5d08ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200515"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>HOW TO：根據繫結項目的清單產生值
<xref:System.Windows.Data.MultiBinding> 可讓您將繫結目標屬性繫結來源屬性的清單，然後套用邏輯以產生具有指定的輸入值。 此範例示範如何使用<xref:System.Windows.Data.MultiBinding>。  
  
## <a name="example"></a>範例  
 在下列範例中，`NameListData` 參考 `PersonName` 物件的集合，這些物件都包含兩個屬性：`firstName` 和 `lastName`。 下列範例會產生<xref:System.Windows.Controls.TextBlock>，會顯示第一個和最後一個名稱的個人姓氏第一個。  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 為了解姓氏-名字格式是如何產生，我們一起看看 `NameConverter` 的實作：  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` 會實作 <xref:System.Windows.Data.IMultiValueConverter> 介面。 `NameConverter` 會從個別繫結取得值，然後將這些值儲存在 values 物件陣列中。 順序<xref:System.Windows.Data.Binding>項目會出現在<xref:System.Windows.Data.MultiBinding>項目是陣列中儲存這些值的順序。 值<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>的 [參數] 引數所參考屬性<xref:System.Windows.Data.MultiBinding.Converter%2A>方法，對參數以決定如何格式化名稱的參數。  
  
## <a name="see-also"></a>另請參閱

- [轉換繫結的資料](how-to-convert-bound-data.md)
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
