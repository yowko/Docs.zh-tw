---
title: HOW TO：在設計階段設定 Windows Forms 的控制項工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 0d6725fc1a00826870e6400bffce63a1788e802c
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211691"
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>HOW TO：在設計階段設定 Windows Form 上控制項的工具提示

您可以設定<xref:System.Windows.Forms.ToolTip>在程式碼，或在 Windows Form 設計工具，在 Visual Studio 中的字串。 如需詳細資訊<xref:System.Windows.Forms.ToolTip>元件，請參閱 < [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)。

## <a name="set-a-tooltip-programmatically"></a>以程式設計方式設定工具提示

1. 新增控制項，將會顯示工具提示。

2. 使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。

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

## <a name="set-a-tooltip-in-the-designer"></a>設定設計工具中的工具提示

1. 在 Visual Studio 中，新增<xref:System.Windows.Forms.ToolTip>元件至表單。

2. 選取的控制項，將會顯示工具提示，或將它新增至表單。

3. 在 **屬性**視窗中，將**ToolTip1 的**適當的文字字串的值。

### <a name="to-remove-a-tooltip-programmatically"></a>若要以程式設計方式移除工具提示

1. 使用<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>方法的<xref:System.Windows.Forms.ToolTip>元件。

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

## <a name="remove-a-tooltip-in-the-designer"></a>在設計工具中移除的工具提示

1. 在 Visual Studio 中，選取 顯示工具提示控制項。

2. 在 [**屬性**] 視窗中，刪除中的文字**ToolTip1 的**。

## <a name="see-also"></a>另請參閱

- [ToolTip 元件概觀](tooltip-component-overview-windows-forms.md)
- [如何：變更 Windows Form ToolTip 元件的延遲時間](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
- [ToolTip 元件](tooltip-component-windows-forms.md)
