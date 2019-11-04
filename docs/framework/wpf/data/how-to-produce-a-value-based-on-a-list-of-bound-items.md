---
title: 操作說明：根據繫結項目的清單產生值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459689"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>操作說明：根據繫結項目的清單產生值
<xref:System.Windows.Data.MultiBinding> 可讓您將系結目標屬性系結至來源屬性的清單，然後套用邏輯以產生具有指定輸入的值。 這個範例示範如何使用 <xref:System.Windows.Data.MultiBinding>。  
  
## <a name="example"></a>範例  
 在下列範例中，`NameListData` 參考 `PersonName` 物件的集合，這些物件都包含兩個屬性：`firstName` 和 `lastName`。 下列範例會產生一個 <xref:System.Windows.Controls.TextBlock>，其中會先顯示姓氏的名字和姓氏。  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 為了解姓氏-名字格式是如何產生，我們一起看看 `NameConverter` 的實作：  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` 會實作 <xref:System.Windows.Data.IMultiValueConverter> 介面。 `NameConverter` 會從個別繫結取得值，然後將這些值儲存在 values 物件陣列中。 <xref:System.Windows.Data.Binding> 專案出現在 <xref:System.Windows.Data.MultiBinding> 元素之下的順序，就是這些值儲存在陣列中的順序。 <xref:System.Windows.Data.MultiBinding.Converter%2A> 方法的參數引數會參考 <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> 屬性的值，它會在參數上執行切換，以決定如何格式化名稱。  
  
## <a name="see-also"></a>請參閱

- [轉換繫結的資料](how-to-convert-bound-data.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
