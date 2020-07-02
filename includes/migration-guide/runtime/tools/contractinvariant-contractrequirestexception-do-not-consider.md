---
ms.openlocfilehash: 29c66edfeb1690199aac39b9c3076d161b2075d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621150"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure

#### <a name="details"></a>詳細資料

針對以 .NET Framework 4.6.1 為目標的應用程式，如果的非變異合約 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 或的前置條件合約 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> 呼叫 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，重寫器會發出編譯器警告 CC1036：偵測 &quot; 到方法 ' system.string.isnullorwhitespace system.string （system.string） ' 沒有 [純] 的呼叫。 &quot;這是編譯器警告，而不是編譯器錯誤。

#### <a name="suggestion"></a>建議

[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。 若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。 您可以在頁面底部找到下載資訊。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.6.1|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
