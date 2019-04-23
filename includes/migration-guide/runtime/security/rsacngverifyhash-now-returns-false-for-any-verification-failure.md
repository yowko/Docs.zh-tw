---
ms.openlocfilehash: acf4e8df2cef3d9ec5d123a14cc7bfcd6f1bfb8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803470"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a>RSACng.VerifyHash 現在會針對任何驗證失敗傳回 False

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.6.2 開始，如果簽章本身的格式不正確，此方法會傳回 <strong>False</strong>。 現在任何驗證失敗都會傳回 False。在 .NET Framework 4.6 和 4.6.1 中，如果簽章本身的格式不正確，此方法會擲回 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>。|
|建議|如果驗證失敗且此方法傳回 <strong>False</strong>，應改為執行任何仰賴處理 <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> 來執行的程式碼。|
|範圍|次要|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
