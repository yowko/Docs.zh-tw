---
title: 作法：在 ToolStrip 控制項中建立切換按鈕
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972359"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>作法：在 ToolStrip 控制項中建立切換按鈕

當使用者按一下切換按鈕時, 它會顯示為凹陷, 並會保留凹陷的外觀, 直到使用者再次按一下按鈕為止。

## <a name="to-create-a-toggling-toolstripbutton"></a>建立切換 ToolStripButton

- 使用程式碼, 如下列程式碼範例所示。 此程式碼假設您的表單<xref:System.Windows.Forms.ToolStrip>包含控制項, 而且其<xref:System.Windows.Forms.ToolStrip.Items%2A>集合包含名<xref:System.Windows.Forms.ToolStripButton> `toolStripButton1`為的。 它也假設您有一個稱為`toolStripButton1_CheckedChanged`的事件處理常式。

    ```vb
    toolStripButton1.CheckOnClick = True
    toolStripButton1.CheckedChanged AddressOf _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

    ```csharp
    toolStripButton1.CheckOnClick = true;
    toolStripButton1.CheckedChanged += new _
    EventHandler(toolStripButton1_CheckedChanged);
    ```

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripButton>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
