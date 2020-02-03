---
title: 變更工具提示元件的延遲
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
ms.openlocfilehash: 8ab0b0760e8c82d752eaada19f14cae57fa63fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746584"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>如何：變更 Windows Form ToolTip 元件的延遲時間
您可以為 Windows Forms <xref:System.Windows.Forms.ToolTip> 元件設定多個延遲值。 所有這些屬性的測量單位為毫秒。 [<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>] 屬性會決定使用者必須指向相關聯控制項的時間，才會出現工具提示字串。 <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 屬性會設定當滑鼠從一個工具提示相關聯的控制項移至另一個時，後續工具提示字串所需的毫秒數。 [<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>] 屬性會決定工具提示字串的顯示時間長度。 您可以個別設定這些值，或藉由設定 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值;其他延遲屬性則是根據指派給 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性的值來設定。 例如，當 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 設定為 n 值時，<xref:System.Windows.Forms.ToolTip.InitialDelay%2A> 設定為 N，<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> 設定為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 除以五（或 N/5）的值，而 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> 設定為 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> 屬性（或5N）的五倍值。  
  
### <a name="to-set-the-delay"></a>若要設定延遲  
  
1. 設定下列屬性，如這個範例所示。  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>另請參閱

- [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)
- [操作說明：在設計階段設定 Windows Forms 上控制項的工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip 元件](tooltip-component-windows-forms.md)
