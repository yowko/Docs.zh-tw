---
title: 如何：在設計階段設定 Windows Form 上控制項的工具提示
description: 瞭解如何在 Visual Studio 中以程式設計方式或在 Windows Form 設計工具中設定控制項的工具提示。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 15134b38d11de30d0e6a2f998f6ea266affc40d7
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325968"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>如何：在設計階段設定 Windows Form 上控制項的工具提示

您可以在程式 <xref:System.Windows.Forms.ToolTip> 代碼中，或在 Visual Studio 的 Windows Form 設計工具中設定字串。 如需元件的詳細資訊 <xref:System.Windows.Forms.ToolTip> ，請參閱[工具提示元件總覽](tooltip-component-overview-windows-forms.md)。

## <a name="set-a-tooltip-programmatically"></a>以程式設計方式設定工具提示

1. 加入將顯示工具提示的控制項。

2. 使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 元件的方法 <xref:System.Windows.Forms.ToolTip> 。

    ```vb
    ' In this example, Button1 is the control to display the ToolTip.
    ToolTip1.SetToolTip(Button1, "Save changes")
    ```

    ```csharp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1.SetToolTip(button1, "Save changes");
    ```

    ```cpp
    // In this example, button1 is the control to display the ToolTip.
    toolTip1->SetToolTip(button1, "Save changes");
    ```

## <a name="set-a-tooltip-in-the-designer"></a>在設計工具中設定工具提示

1. 在 Visual Studio 中，將 <xref:System.Windows.Forms.ToolTip> 元件新增至表單。

2. 選取要顯示工具提示的控制項，或將它新增至表單。

3. 在 [**屬性**] 視窗中，將 [ToolTip1 值]**上的工具提示**設定為適當的文字字串。

### <a name="to-remove-a-tooltip-programmatically"></a>以程式設計方式移除工具提示

1. 使用 <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> 元件的方法 <xref:System.Windows.Forms.ToolTip> 。

    ```vb
    ' In this example, Button1 is the control displaying the ToolTip.
    ToolTip1.SetToolTip(Button1, Nothing)
    ```

    ```csharp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1.SetToolTip(button1, null);
    ```

    ```cpp
    // In this example, button1 is the control displaying the ToolTip.
    toolTip1->SetToolTip(button1, NULL);
    ```

## <a name="remove-a-tooltip-in-the-designer"></a>移除設計師中的工具提示

1. 在 [Visual Studio 中，選取顯示工具提示的控制項。

2. 在 [**屬性**] 視窗中，刪除**ToolTip1 上工具提示**中的文字。

## <a name="see-also"></a>另請參閱

- [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)
- [操作說明：變更 Windows Forms ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip 元件](tooltip-component-windows-forms.md)
