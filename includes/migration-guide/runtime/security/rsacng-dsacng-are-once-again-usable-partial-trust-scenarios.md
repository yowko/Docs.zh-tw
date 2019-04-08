---
ms.openlocfilehash: 242a9952cb47d170aceffa1aa392071eb40cc6ab
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760622"
---
### <a name="rsacng-and-dsacng-are-once-again-usable-in-partial-trust-scenarios"></a>RSACng 和 DSACng 再次可在部分信任案例中使用

|   |   |
|---|---|
|詳細資料|CngLightup (用於數個較高層級的加密 API，例如 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType>) 和 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> 在某些情況下依賴完全信任。 這些包括沒有主張 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 權限的 P/Invoke，以及 <xref:System.Security.Cryptography.CngKey?displayProperty=nameWithType> 具有 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode?displayProperty=nameWithType> 之權限要求的程式碼路徑。 從 .NET Framework 4.6.2 開始，盡量使用 CngLightup 來切換至 <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType>。 因此，成功使用 <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=nameWithType> 的部分信任應用程式開始失敗，並擲回 <xref:System.Security.SecurityException> 例外狀況。這項變更將新增所需的主張，讓所有使用 CngLightup 的函式具有必要權限。|
|建議|如果 .NET Framework 4.6.2 中的這項變更已對部分信任應用程式產生負面影響，請升級至 .NET Framework 4.7.1。|
|範圍|Edge|
|版本|4.6.2|
|類型|執行階段|
|受影響的 API|<ul><li><xref:System.Security.Cryptography.DSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.LegalKeySizes?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.CreateSignature(System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.DSACng.VerifySignature(System.Byte[],System.Byte[])?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.%23ctor(System.Security.Cryptography.CngKey)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Key?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.Decrypt(System.Byte[],System.Security.Cryptography.RSAEncryptionPadding)?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.RSACng.SignHash(System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

