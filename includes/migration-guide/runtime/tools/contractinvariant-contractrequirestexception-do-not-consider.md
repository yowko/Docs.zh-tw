---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478291"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure

#### <a name="details"></a>詳細資料

針對以 .NET Framework 4.6.1 為目標的應用程式，如果的非變異合約 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 或呼叫方法的前置條件合約 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> ，重寫器 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 會發出編譯器警告 CC1036：偵測 &quot; 到方法 ' System.string. IsNullOrWhiteSpace (system.string) ' 的呼叫，但方法中沒有 [純]。 &quot; 這是編譯器警告，而不是編譯器錯誤。

#### <a name="suggestion"></a>建議

[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。 若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。 您可以在頁面底部找到下載資訊。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.1|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
