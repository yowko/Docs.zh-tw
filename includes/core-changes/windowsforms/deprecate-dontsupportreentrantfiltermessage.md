---
ms.openlocfilehash: cb72e1b92172b8989ce99b47181c13561a7ccd76
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181823"
---
### <a name="switchsystemwindowsformsdontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>不支援 DontSupportReentrantFilterMessage 相容性參數

.Net `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.6.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`開始，相容性參數會解決以自訂<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>執行<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>呼叫訊息時可能發生<xref:System.IndexOutOfRangeException>的例外狀況。 如需詳細資訊，請參閱[風險降低：自訂 Imessagefilter.prefiltermessage Imessagefilter.prefiltermessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)的執行。

在 .net Core 中， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
