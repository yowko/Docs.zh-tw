---
ms.openlocfilehash: fc0eec26073c299887b4748d0ad37e21c7294e84
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275137"
---
### <a name="winforms-apis-now-throw-argumentnullexception"></a>WinForms API 現在引發參數無效

一個 Windows 的<xref:System.ArgumentNullException>相檔方法為 null 參數<xref:System.NullReferenceException>引發一個參數, 它會引發一個 。

#### <a name="change-description"></a>變更描述

以前,某些 Windows 窗<xref:System.NullReferenceException>體方法 引發 if 傳遞了 null 的參數。 從 .NET 5.0 開始,<xref:System.ArgumentNullException>這些方法現在將改為為 null 參數。

引發<xref:System.ArgumentNullException>符合 .NET 運行時的行為。 它還通過清楚地傳達參數為空以及參數為空來改善調試體驗。

#### <a name="version-introduced"></a>介紹的版本

.NET 5.0 預覽 1*
.NET 5.0 預覽 2

#### <a name="recommended-action"></a>建議的動作

如果呼叫這些方法中的任何一個,並且代碼目前捕捉<xref:System.NullReferenceException>for null 參數,請<xref:System.ArgumentNullException>改為 捕捉 。 此外,請考慮更新代碼以防止將空參數傳遞給列出的方法。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

從 .NET 5.0 預覽 1 開始:

- <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)>
- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType>

從 .NET 5.0 預覽 2 開始:

- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType>( 僅<xref:System.IO.Stream>適用於參數 )

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`

-->
