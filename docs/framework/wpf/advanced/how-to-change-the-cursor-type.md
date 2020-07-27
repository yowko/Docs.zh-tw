---
title: 如何：變更游標類型
description: 變更專案的滑鼠指標游標以及 Windows Presentation Foundation 中的應用程式。 這個範例包含 XAML 和程式碼後置檔案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165959"
---
# <a name="how-to-change-the-cursor-type"></a>如何：變更游標類型
這個範例會示範如何變更特定專案的 <xref:System.Windows.Input.Cursor> 滑鼠指標，以及應用程式的。  
  
 這個範例包含檔案 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼後置檔案。  
  
## <a name="example"></a>範例  
 使用者介面是由所建立，其中包含 <xref:System.Windows.Controls.ComboBox> 要選取所需的 <xref:System.Windows.Input.Cursor> 、一組 <xref:System.Windows.Controls.RadioButton> 物件，以判斷游標變更僅適用于單一專案，還是套用至整個應用程式，而是新資料 <xref:System.Windows.Controls.Border> 指標套用的元素。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 下列程式碼後置會建立一個 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件處理常式，當中的資料指標類型變更時，就會呼叫它 <xref:System.Windows.Controls.ComboBox> 。  Switch 語句會篩選游標名稱，並在 <xref:System.Windows.FrameworkElement.Cursor%2A> <xref:System.Windows.Controls.Border> 名為*DisplayArea*的上設定屬性。  
  
 如果資料指標變更設定為「整個應用程式」，則 <xref:System.Windows.Input.Mouse.OverrideCursor%2A> 屬性會設定為 <xref:System.Windows.FrameworkElement.Cursor%2A> 控制項的屬性 <xref:System.Windows.Controls.Border> 。  這會強制變更整個應用程式的游標。  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
