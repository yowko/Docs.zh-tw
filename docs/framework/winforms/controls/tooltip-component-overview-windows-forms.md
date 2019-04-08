---
title: ToolTip 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 3fbe883501d1ce36ca25ea07631f98042f451e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197304"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip 元件概觀 (Windows Form)
當使用者指向控制項時，Windows Form <xref:System.Windows.Forms.ToolTip> 元件會顯示文字。 工具提示可以與任何控制項產生關聯。 使用此元件的範例： 為了節省空間，在表單上，您可以按鈕上顯示的小圖示，並使用工具提示說明按鈕的功能。  
  
## <a name="working-with-the-tooltip-component"></a>使用 ToolTip 元件  
 A<xref:System.Windows.Forms.ToolTip>元件提供`ToolTip`Windows 表單或其他容器上的多個控制項的屬性。 比方說，如果您將其中一個放<xref:System.Windows.Forms.ToolTip>表單上的元件，您可以顯示"輸入您的名稱 」<xref:System.Windows.Forms.TextBox>控制和"按一下此處以儲存變更"<xref:System.Windows.Forms.Button>控制項。  
  
 主要方法<xref:System.Windows.Forms.ToolTip>元件<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>和<xref:System.Windows.Forms.ToolTip.GetToolTip%2A>。 您可以使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法來設定顯示控制項的工具提示。 如需詳細資訊，請參閱[如何：設定 Windows Form 上控制項的工具提示，在設計階段](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)。 索引鍵屬性是<xref:System.Windows.Forms.ToolTip.Active%2A>，且必須設為`true`才會出現，工具提示和<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>、 可設定的工具提示字串會顯示的時間長度、 多久才會出現，工具提示控制項必須指向使用者和時間的方式需要後續工具提示視窗出現的時間。 如需詳細資訊，請參閱[如何：變更 Windows Form ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolTip>
- [HOW TO：在設計階段設定 Windows Forms 的控制項工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [HOW TO：變更 Windows Forms ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
