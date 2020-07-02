---
ms.openlocfilehash: d587e542a72d584502ac3ac892619cc38b88ef77
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619923"
---
### <a name="httputilityjavascriptstringencode-escapes-ampersand"></a>HttpUtility.JavaScriptStringEncode 會逸出 & 符號

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=fullName> 會逸出 &amp; 字元。

#### <a name="suggestion"></a>建議

如果您的應用程式相依於此方法的舊版行為，您可以將 aspnet:JavaScriptDoNotEncodeAmpersand 設定新增至組態檔中的 [ASP.NET appSettings 項目](https://docs.microsoft.com/previous-versions/aspnet/hh975440(v=vs.120))。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Web.HttpUtility.JavaScriptStringEncode(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
