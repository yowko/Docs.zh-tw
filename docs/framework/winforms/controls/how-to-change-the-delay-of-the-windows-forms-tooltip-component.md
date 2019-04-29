---
title: HOW TO：變更 Windows Forms ToolTip 元件的延遲時間
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
ms.openlocfilehash: cf257cccd272c16c3d7c3d403456265444fc8ac8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781234"
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>HOW TO：變更 Windows Forms ToolTip 元件的延遲時間
有多個您可以設定 Windows Form 的延遲值<xref:System.Windows.Forms.ToolTip>元件。 所有這些屬性的測量單位為毫秒。 <xref:System.Windows.Forms.ToolTip.InitialDelay%2A>屬性會決定使用者必須指向相關聯的控制項才會出現工具提示字串的時間長度。 <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>屬性會設定後續的工具提示字串，以顯示當滑鼠移動到另一個工具提示相關聯的控制項中所花費的毫秒數。 <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>屬性會決定的工具提示字串會顯示的時間長度。 您可以個別或藉由設定的值來設定這些值<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性; 屬性會根據設定的值指派給其他延遲<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性。 例如，當<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>設為值 N，<xref:System.Windows.Forms.ToolTip.InitialDelay%2A>設定為 N，<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A>設定的值為<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>除以五個 （或 N/5），並<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A>值是五倍的值，這個值會設<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>屬性 （或 5N）。  
  
### <a name="to-set-the-delay"></a>若要設定的延遲  
  
1. 在此範例中所示，請設定下列屬性。  
  
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
- [如何：在設計階段設定 Windows Form 上控制項的工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [ToolTip 元件](tooltip-component-windows-forms.md)
