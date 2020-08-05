---
ms.openlocfilehash: 95aa243a5790d4201c7871e617dbe4ccafb7c1a1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556147"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>不支援 DontSupportReentrantFilterMessage 相容性切換

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.Net Core 和 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.6.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 開始， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 相容性參數 <xref:System.IndexOutOfRangeException> 會解決 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 以自訂執行呼叫訊息時可能發生的例外狀況 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 不支援此參數。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message)`

-->
