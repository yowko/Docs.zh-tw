---
ms.openlocfilehash: 2c44c2e1658f8de556d3f7222de3fa6d4594163a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496617"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>將在 .NET Framework 4.5 下序列化的 MailMessage 物件還原序列化可能會失敗

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，<xref:System.Web.Mail.MailMessage> 物件可以包含非 ASCII 字元。 在 .NET Framework 4 中，僅支援 ASCII 字元。 包含非 ASCII 字元且在 .NET Framework 4.5 或更新版本下序列化的 <xref:System.Web.Mail.MailMessage> 物件，無法在 .NET Framework 4 下還原序列化。

#### <a name="suggestion"></a>建議

請確定您的程式碼在將 <xref:System.Web.Mail.MailMessage> 物件還原序列化時，會提供例外狀況處理。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.5|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Web.Mail.MailMessage`

-->
