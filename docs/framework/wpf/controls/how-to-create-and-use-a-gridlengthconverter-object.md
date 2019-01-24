---
title: HOW TO：建立和使用 GridLengthConverter 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: b5ab15df4aaf5f6c4ba7bc7a4b36cc5e122b1320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562049"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>HOW TO：建立和使用 GridLengthConverter 物件
## <a name="example"></a>範例  
 下列範例示範如何建立和使用的執行個體<xref:System.Windows.GridLengthConverter>。 此範例會定義呼叫的自訂方法`changeCol`，哪一個階段<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.GridLengthConverter>可將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.GridLength>。 已轉換的值傳遞的值<xref:System.Windows.Controls.ColumnDefinition.Width%2A>屬性<xref:System.Windows.Controls.ColumnDefinition>項目。  
  
 此範例也會定義第二個的自訂方法，稱為`changeColVal`。 這個自訂的方法轉換<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>的<xref:System.Windows.Controls.Slider>要<xref:System.String>和傳遞的值將會回到<xref:System.Windows.Controls.ColumnDefinition>做為<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的項目。  
  
 請注意，個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案中定義的內容<xref:System.Windows.Controls.ListBoxItem>。  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
