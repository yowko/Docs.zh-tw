---
title: HOW TO：使用焦點事件變更項目的色彩
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004831"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>HOW TO：使用焦點事件變更項目的色彩
這個範例示範如何在專案取得和失去焦點時，使用 <xref:System.Windows.UIElement.GotFocus> 和 <xref:System.Windows.UIElement.LostFocus> 事件來變更元素的色彩。  
  
 這個範例是由 @no__t 0 檔案和程式碼後置檔案所組成。  
  
## <a name="example"></a>範例  
 下列 XAML 會建立使用者介面，其中包含兩個 @no__t 0 的物件，並將 <xref:System.Windows.UIElement.GotFocus> 和 @no__t 2 事件的事件處理常式附加至 <xref:System.Windows.Controls.Button> 物件。  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 下列程式碼後置會建立 <xref:System.Windows.UIElement.GotFocus> 和 @no__t 1 事件處理常式。  當 @no__t 0 取得鍵盤焦點時，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 會變更為紅色。  當 @no__t 0 失去鍵盤焦點時，<xref:System.Windows.Controls.Button> 的 <xref:System.Windows.Controls.Control.Background%2A> 會變更回白色。  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>另請參閱

- [輸入概觀](input-overview.md)
