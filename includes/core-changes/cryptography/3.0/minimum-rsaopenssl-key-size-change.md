---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568000"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>RSAOpenSsl 金鑰生成的最低大小已增加

在 Linux 上生成新 RSA 金鑰的最小大小從 384 位增加到 512 位。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0`LegalKeySizes`開始，屬性在 RSA 實例上報告的最小法律<xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>金鑰<xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>大小從<xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>、和 Linux 上從 384 增加到 512。

因此，在 .NET Core 2.2 和早期版本中，方法調用（`RSA.Create(384)`如成功）將成功。 在 .NET Core 3.0 和更高版本中`RSA.Create(384)`，方法調用將引發一個異常，指示大小太小。

之所以做出此更改，是因為在 Linux 上執行加密操作的 OpenSSL 在版本 1.0.2 和 1.1.0 之間提高了最小值。 .NET Core 3.0 更喜歡 OpenSSL 1.1.x 到 1.0.x，並且提出了最低報告版本以反映這種新的更高依賴項限制。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

如果調用任何受影響的 API，請確保任何生成的金鑰的大小不小於提供程式的最小值。

> [!NOTE]
> 384 位 RSA 已被視為不安全（如 512 位 RSA）。 現代建議，如[NIST 特別出版物 800-57 第 1 部分修訂版 4，](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)建議將 2048 位作為新生成的金鑰的最小大小。

#### <a name="category"></a>類別

Cryptography

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
