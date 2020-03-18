---
ms.openlocfilehash: 3272dc562981269b868df4ca9d3a5806918aba5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937102"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>不支援不支援重新進入篩選器消息相容性開關

.NET 框架 4.6.1 中引入的`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET 框架 4.6.1`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`開始，相容性開關解決了<xref:System.IndexOutOfRangeException>使用自訂<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>實現調用<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>消息時可能出現的異常。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。

在 .NET 內核`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`中，不支援交換器。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
