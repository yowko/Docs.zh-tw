---
title: 作法：使用設計工具以 Windows Forms Panel 控制項分組控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040379"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a>作法：使用設計工具以 Windows Forms Panel 控制項分組控制項
Windows Forms <xref:System.Windows.Forms.Panel>控制項是用來將其他控制項分組。 群組控制項的原因有三個。 其中一個是明確使用者介面的相關表單元素的視覺化群組;另一個是以程式設計方式分組, 例如選項按鈕,最後一個是在設計階段將控制項移動為一個單位。

## <a name="to-create-a-group-of-controls"></a>若要建立控制項群組

1. 將控制項從 [工具箱] 的 [Windows Forms] 索引標籤拖曳到表單上。 <xref:System.Windows.Forms.Panel>

2. 將其他控制項新增至面板, 並在面板內繪製每個控制項。

     如果您有想要放在面板中的現有控制項, 您可以選取所有控制項、將其剪下至剪貼簿、選取<xref:System.Windows.Forms.Panel>控制項, 然後將其貼到面板中。 您也可以將它們拖曳至面板。

3. 選擇性如果您想要將框線新增至面板, 請設定其<xref:System.Windows.Forms.BorderStyle>屬性。 有三個選擇: <xref:System.Windows.Forms.BorderStyle.Fixed3D>、 <xref:System.Windows.Forms.BorderStyle.FixedSingle>和<xref:System.Windows.Forms.BorderStyle.None>。

## <a name="see-also"></a>另請參閱

- [Panel 控制項](panel-control-windows-forms.md)
- [Panel 控制項概觀](panel-control-overview-windows-forms.md)
- [如何：設定面板的背景](how-to-set-the-background-of-a-windows-forms-panel.md)
