---
title: HOW TO：使用 FontSizeConverter 類別
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 7cb76ad4ffe4b4574a48212240b852e1f2253088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741895"
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>HOW TO：使用 FontSizeConverter 類別
## <a name="example"></a>範例  
 此範例示範如何建立的執行個體<xref:System.Windows.FontSizeConverter>並用它來變更字型大小。  
  
 此範例會定義呼叫的自訂方法`changeSize`可將轉換的內容<xref:System.Windows.Controls.ListBoxItem>，因為定義於個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Double>，和更新版本到<xref:System.String>。 此方法會傳遞<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.FontSizeConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>。 此值接著會傳遞的值<xref:System.Windows.Controls.TextBlock.FontSize%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。  
  
 此範例也會定義第二個自訂方法，稱為`changeFamily`。 這個方法會轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>要<xref:System.String>，然後將該值傳遞<xref:System.Windows.Controls.TextBlock.FontFamily%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。  
  
 此範例不會執行。  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.FontSizeConverter>
