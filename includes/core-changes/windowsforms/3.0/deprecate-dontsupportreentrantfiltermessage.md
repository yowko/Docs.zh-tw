---
ms.openlocfilehash: 55c13aa70a03bcc548ce1d096cca8f40de6cda84
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720983"
---
### <a name="dontsupportreentrantfiltermessage-compatibility-switch-not-supported"></a>不支援 DontSupportReentrantFilterMessage 相容性切換

`Switch.System.Windows.Forms.DontSupportReentrantFilterMessage`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.6.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.6.1 開始， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 相容性參數 <xref:System.IndexOutOfRangeException> 會解決 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 以自訂執行呼叫訊息時可能發生的例外狀況 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 。 如需詳細資訊，請參閱[風險降低：自訂 IMessageFilter.PreFilterMessage 實作](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。

在 .NET Core 中， `Switch.System.Windows.Forms.DontSupportReentrantFilterMessage` 不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

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
