---
title: "如何：變更游標類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c59f4c90eed00775fc9fceaf872391faa93784
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-cursor-type"></a>如何：變更游標類型
這個範例示範如何變更<xref:System.Windows.Input.Cursor>滑鼠指標特定的項目和應用程式。  
  
 這個範例包含[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案和程式碼後置檔案。  
  
## <a name="example"></a>範例  
 建立使用者介面，其中包含的<xref:System.Windows.Controls.ComboBox>來選取所需<xref:System.Windows.Input.Cursor>，一組<xref:System.Windows.Controls.RadioButton>物件來判斷是否資料指標變更套用至單一項目，或套用至整個應用程式，以及<xref:System.Windows.Controls.Border>這是新的資料指標會套用至的項目。  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 下列程式碼後置建立<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>中變更的資料指標類型，就會呼叫事件處理常式<xref:System.Windows.Controls.ComboBox>。  Switch 陳述式的篩選集與資料指標名稱<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>這名為*DisplayArea*。  
  
 如果資料指標變更設定為 「 整個應用程式 」<xref:System.Windows.Input.Mouse.OverrideCursor%2A>屬性設定為<xref:System.Windows.FrameworkElement.Cursor%2A>屬性<xref:System.Windows.Controls.Border>控制項。  這會強制變更整個應用程式的游標。  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>請參閱  
 [輸入概觀](../../../../docs/framework/wpf/advanced/input-overview.md)
