---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496462"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False

#### <a name="details"></a>詳細資料

從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 **False**。 現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName>。

#### <a name="suggestion"></a>建議

如果驗證失敗且此方法傳回 **False**，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> 來執行的程式碼。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   |Minor|
|版本|4.6.2|
|類型|執行階段|

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
