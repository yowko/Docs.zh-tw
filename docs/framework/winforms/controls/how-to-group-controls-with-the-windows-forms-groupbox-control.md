---
title: 具有分組控制項的群組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
ms.openlocfilehash: bb7476c410d2802b5d32cc9842a778f290765e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736660"
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>如何：以 Windows Form GroupBox 控制項來群組控制項
Windows Forms <xref:System.Windows.Forms.GroupBox> 控制項用來分組其他控制項。 群組控制項的原因有三個：  
  
- 為明確的使用者介面建立相關表單元素的視覺化群組。  
  
- 建立程式設計群組（例如選項按鈕）。  
  
- 用於在設計階段將控制項移動為一個單位。  
  
### <a name="to-create-a-group-of-controls"></a>若要建立控制項群組  
  
1. 在表單上繪製 <xref:System.Windows.Forms.GroupBox> 控制項。  
  
2. 將其他控制項新增至 [群組] 方塊，並在 [群組方塊] 內繪製每個控制項。  
  
     如果您有想要放在群組方塊中的現有控制項，您可以選取所有控制項、將其剪下至剪貼簿、選取 [<xref:System.Windows.Forms.GroupBox>] 控制項，然後將它們貼到 [群組] 方塊中。 您也可以將它們拖曳到 [群組] 方塊中。  
  
3. 將 [群組方塊] 的 [<xref:System.Windows.Forms.GroupBox.Text%2A>] 屬性設定為適當的標題。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.GroupBox>
- [GroupBox 控制項](groupbox-control-windows-forms.md)
