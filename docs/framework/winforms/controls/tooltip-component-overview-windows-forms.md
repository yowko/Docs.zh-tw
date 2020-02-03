---
title: ToolTip 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741911"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip 元件概觀 (Windows Form)
當使用者指向控制項時，Windows Form <xref:System.Windows.Forms.ToolTip> 元件會顯示文字。 工具提示可以與任何控制項產生關聯。 使用此元件的範例：若要在表單上儲存空間，您可以在按鈕上顯示一個小圖示，並使用工具提示來說明按鈕的功能。  
  
## <a name="working-with-the-tooltip-component"></a>使用工具提示元件  
 <xref:System.Windows.Forms.ToolTip> 元件會提供 `ToolTip` 屬性給 Windows Form 或其他容器上的多個控制項。 例如，如果您將一個 <xref:System.Windows.Forms.ToolTip> 元件放在表單上，您可以在 <xref:System.Windows.Forms.TextBox> 控制項中顯示「在此輸入您的名稱」，然後在 <xref:System.Windows.Forms.Button> 控制項中，針對 [按一下這裡儲存變更]。  
  
 <xref:System.Windows.Forms.ToolTip> 元件的主要方法是 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 和 <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>。 您可以使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 方法來設定針對控制項顯示的工具提示。 如需詳細資訊，請參閱[如何：在設計階段設定 Windows Form 上控制項的工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)。 索引鍵屬性是 <xref:System.Windows.Forms.ToolTip.Active%2A>的，其必須設定為 `true`，工具提示才會出現，而 <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>則會設定顯示工具提示字串的時間長度、使用者必須指向控制項以顯示工具提示，以及後續工具提示視窗出現的時間長短。 如需詳細資訊，請參閱[如何：變更 Windows Forms 工具提示元件的延遲](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolTip>
- [操作說明：在設計階段設定 Windows Forms 上控制項的工具提示](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [操作說明：變更 Windows Forms ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
