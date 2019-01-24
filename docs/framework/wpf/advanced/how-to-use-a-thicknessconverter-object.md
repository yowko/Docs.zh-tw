---
title: HOW TO：使用 ThicknessConverter 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: 22215a155f4a204e3edeebc464413d5718290bb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577067"
---
# <a name="how-to-use-a-thicknessconverter-object"></a>HOW TO：使用 ThicknessConverter 物件
## <a name="example"></a>範例  
 此範例示範如何建立的執行個體<xref:System.Windows.ThicknessConverter>並用它來變更框線的粗細。  
  
 此範例會定義呼叫的自訂方法`changeThickness`; 這個方法會先將轉換的內容<xref:System.Windows.Controls.ListBoxItem>，因為定義於個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Windows.Thickness>，並稍後將轉換成內容<xref:System.String>。 此方法會傳遞<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.ThicknessConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.Thickness>。 此值接著會傳遞的值<xref:System.Windows.Controls.Border.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。  
  
 此範例不會執行。  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- [如何：變更邊界屬性](https://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)
- [如何：轉換成新的資料類型的 ListBoxItem](https://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)
- [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
