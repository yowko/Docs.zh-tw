---
title: 如何：管理 ToolStrip 溢位
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736141"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a>如何：管理 Windows Form 中的 ToolStrip 溢位

當 <xref:System.Windows.Forms.ToolStrip> 控制項上的所有專案都無法納入配置的空間時，您可以在 <xref:System.Windows.Forms.ToolStrip> 上啟用溢位功能，並判斷特定 <xref:System.Windows.Forms.ToolStripItem>的溢位行為。

當您加入的 <xref:System.Windows.Forms.ToolStripItem>需要比配置給 <xref:System.Windows.Forms.ToolStrip> 的空間，並指定表單的目前大小，<xref:System.Windows.Forms.ToolStripOverflowButton> 會自動出現在 <xref:System.Windows.Forms.ToolStrip>上。 此時會出現 <xref:System.Windows.Forms.ToolStripOverflowButton>，而且已啟用溢位的專案會移至下拉式 溢位 功能表中。 這可讓您自訂 <xref:System.Windows.Forms.ToolStrip> 專案適當調整成不同表單大小的方式，並設定其優先順序。 您也可以使用 [<xref:System.Windows.Forms.ToolStripItem.Placement%2A>] 和 [<xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> 屬性] 和 [<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>] 事件，在專案落入溢位時變更其外觀。 如果您在設計階段或執行時間放大表單，主要 <xref:System.Windows.Forms.ToolStrip> 上可以顯示更多 <xref:System.Windows.Forms.ToolStripItem>，而 <xref:System.Windows.Forms.ToolStripOverflowButton> 甚至可能會消失，直到您減少表單的大小。

## <a name="to-enable-overflow-on-a-toolstrip-control"></a>啟用 ToolStrip 控制項的溢位

- 確定 <xref:System.Windows.Forms.ToolStrip>的 [<xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>] 屬性未設定為 [`false`]。 預設為 `True`。

     當 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> `True` （預設值）時，當 <xref:System.Windows.Forms.ToolStripItem> 的內容超過水準 <xref:System.Windows.Forms.ToolStrip> 的寬度或垂直 <xref:System.Windows.Forms.ToolStrip>的高度時，<xref:System.Windows.Forms.ToolStripItem> 就會傳送至下拉式溢位功能表。

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a>若要指定特定 ToolStripItem 的溢位行為

- 將 <xref:System.Windows.Forms.ToolStripItem> 的 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> 屬性設為所需的值。 可能的情況包括 `Always`、`Never`和 `AsNeeded`。 預設為 `AsNeeded`。

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
