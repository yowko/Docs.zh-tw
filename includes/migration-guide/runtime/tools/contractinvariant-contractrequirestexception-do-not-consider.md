---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237935"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant 或 Contract.Requires\<TException> 不會將 String.IsNullOrEmpty 視為 pure

|   |   |
|---|---|
|詳細資料|對於針對 .NET Framework 4.6.1<xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType>的應用，如果<xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)>調用<xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>方法的不變協定或預置協定，則重新編寫器將發出編譯器警告 CC1036：&quot;檢測到方法"System.String.IsNullOrWhteSpace（System.String）"的調用，而不在方法中 [Pure]。&quot;這是編譯器警告，而不是編譯器錯誤。|
|建議|[GitHub 問題 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已解決這種行為。 若要移除這個警告，您可以從 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下載並編譯程式碼合約工具原始程式碼的更新版本。 您可以在頁面底部找到下載資訊。|
|影響範圍|Minor|
|版本|4.6.1|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
