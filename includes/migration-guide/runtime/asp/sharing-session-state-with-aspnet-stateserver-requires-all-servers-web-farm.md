---
ms.openlocfilehash: e450c53008e7562e37518fdfd6872ff9b63b6ac3
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609126"
---
### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a>使用 ASP.NET StateServer 共用會話狀態需要 web 伺服陣列中的所有伺服器都使用相同的 .NET Framework 版本

#### <a name="details"></a>詳細資料

啟用 <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=fullName> 工作階段狀態時，指定之 Web 伺服陣列中的所有伺服器必須使用相同版本的 .NET Framework，才能正確共用狀態。

#### <a name="suggestion"></a>建議

請務必將共用狀態之 Web 伺服器上的 .NET Framework 版本同時升級。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType>

<!--

#### Affected APIs

- `F:System.Web.SessionState.SessionStateMode.StateServer`

-->
