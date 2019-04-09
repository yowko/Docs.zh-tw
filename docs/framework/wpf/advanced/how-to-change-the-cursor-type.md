---
title: HOW TO：變更游標類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 5c9e6931f6addb62a51e44b06a159d4e7b1e5f8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141202"
---
# <a name="how-to-change-the-cursor-type"></a>HOW TO：變更游標類型
此範例示範如何變更<xref:System.Windows.Input.Cursor>滑鼠指標的特定項目以及應用程式。  
  
 此範例中組成[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
## <a name="example"></a>範例  
 已建立使用者介面，其中包含<xref:System.Windows.Controls.ComboBox>若要選取所需<xref:System.Windows.Input.Cursor>，一組<xref:System.Windows.Controls.RadioButton>物件來判斷是否資料指標變更套用至單一項目，或適用於整個應用程式，和<xref:System.Windows.Controls.Border>這是新的資料指標會套用至的項目。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 建立下列的程式碼後置<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件處理常式中變更的資料指標類型時，會呼叫<xref:System.Windows.Controls.ComboBox>。  Switch 陳述式會篩選的資料指標名稱和集合<xref:System.Windows.FrameworkElement.Cursor%2A>上的屬性<xref:System.Windows.Controls.Border>哪些具名*DisplayArea*。  
  
 如果資料指標變更設定為 「 整個應用程式 」<xref:System.Windows.Input.Mouse.OverrideCursor%2A>屬性設定為<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>控制項。  這會強制變更整個應用程式的游標。  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
