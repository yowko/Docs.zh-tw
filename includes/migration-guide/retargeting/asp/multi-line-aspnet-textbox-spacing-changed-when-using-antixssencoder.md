---
ms.openlocfilehash: 53860bb867522503c5cb9bd35e25fadd00a116a2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609153"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>使用 AntiXSSEncoder 時，多行 ASP.NET 文字方塊間距已變更

#### <a name="details"></a>詳細資料

在 .NET Framework 4.0 中，如果使用 <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>，則會在回傳時，於多行文字方塊的行間插入額外幾行。 在 .NET Framework 4.5 中，不會包含這些額外的分行符號，但前提是 Web 應用程式是以 .NET Framework 4.5 為目標

#### <a name="suggestion"></a>建議

請注意，重定目標為 .NET Framework 4.5 的 4.0 版 Web 應用程式可能已改善多行文字方塊，不再插入額外的分行符號。 如果不想這麼做，在 .NET Framework 4.5 上執行的應用程式可藉由將目標設為 .NET Framework 4.0 來保留舊版行為。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Minor       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |
