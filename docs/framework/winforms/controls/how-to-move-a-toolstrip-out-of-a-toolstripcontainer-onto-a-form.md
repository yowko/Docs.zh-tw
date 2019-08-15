---
title: HOW TO：將 ToolStrip 移出 ToolStripContainer 並移至表單上
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: c6519add6789485d41146633abb5e11f80913649
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039832"
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>作法：將 ToolStrip 移出 ToolStripContainer 並移至表單上
使用下列程式, 將移<xref:System.Windows.Forms.ToolStrip>出<xref:System.Windows.Forms.ToolStripContainer>表單上的。

## <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>將 ToolStrip 移出 ToolStripContainer 到表單上

1. 選取 <xref:System.Windows.Forms.ToolStrip>。

2. 按 CTRL + X, 或<xref:System.Windows.Forms.ToolStrip> 以滑鼠右鍵按一下,然後從內容功能表選擇[剪下],即可剪<xref:System.Windows.Forms.ToolStrip>下。

3. 選取表單。

4. 按 CTRL + V 貼上, 或從 [**編輯**] 功能表選擇 [貼上]。 <xref:System.Windows.Forms.ToolStrip>

5. 將的<xref:System.Windows.Forms.ToolStrip.Dock%2A> <xref:System.Windows.Forms.ToolStrip>屬性設定為**Top**。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
