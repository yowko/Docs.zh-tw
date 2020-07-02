---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617141"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>System.Uri.IsWellFormedUriString 方法針對第一個區段中有冒號字元的相對 URI 會傳回 false

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，<xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> 會將第一個區段中具有 `:` 的相對 URI 視為格式不正確。 這是 .NET Framework 4.0 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 行為的變更，以符合 RFC3986。

#### <a name="suggestion"></a>建議

這項變更 (就像許多其他的 URI 變更一樣) 只會影響以 .NET Framework 4.5 (或更新版本) 為目標的應用程式。 若要繼續使用舊的行為，請將應用程式設為以 .NET Framework 4.0 為目標。 或者，在呼叫 <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> 前掃描 URI，尋找 `:` 字元，如果您偏好舊的行為，則請移除字元以進行驗證。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
