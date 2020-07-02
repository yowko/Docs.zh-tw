---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617523"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath 擲回 NullReferenceException

#### <a name="details"></a>詳細資料

在 .NET Framework 4.6.2 中，執行階段在擷取包含 null 字元的 `P:System.Web.HttpRuntime.AppDomainAppPath` 值時，會擲回 `T:System.NullReferenceException`。在 .NET Framework 4.6.1 和更早版本中，執行階段會擲回 `T:System.ArgumentNullException`。

#### <a name="suggestion"></a>建議

您可以執行下列其中一個動作以回應這項變更︰

- 如果您的應用程式是在 .NET Framework 4.6.2 上執行，請處理 `T:System.NullReferenceException`。
- 升級至 .NET Framework 4.7，這可以還原舊版行為並擲回 `T:System.ArgumentNullException`。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.6.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
