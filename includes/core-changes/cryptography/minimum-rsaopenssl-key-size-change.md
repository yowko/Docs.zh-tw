---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117245"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a>RSAOpenSsl 金鑰產生的大小下限已增加

在 Linux 上產生新 RSA 金鑰的最小大小已從 384-位增加至512位。

#### <a name="change-description"></a>變更描述

從 .net Core 3.0 開始，從 < 系統的 rsa 實例上的`LegalKeySizes`屬性所報告的最小合法金鑰大小。 RSAOpenSsl. Create% 2a？ displayProperty = namewithtype> >，< system.object。23ctor% 2A？ displayProperty = Namewithtype> >，而 < 系統. RSACryptoServicePlatform.% 23ctor% 2A？ displayProperty = Namewithtype> > on Linux 已從384增加至512。

因此，在 .net Core 2.2 和更早版本中，方法呼叫（例如`RSA.Create(384)` ）會成功。 在 .net Core 3.0 和更新版本中，方法呼叫`RSA.Create(384)`會擲回例外狀況，指出大小太小。

已進行此變更，因為 OpenSSL 會在 Linux 上執行密碼編譯作業，並在版本1.0.2 和1.1.0 之間產生最小值。  .NET Core 3.0 傾向于將 OpenSSL 1.1. x 新增至 1.0. x，並產生最小的回報版本，以反映這項較高的相依性限制。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

如果您呼叫任何受影響的 Api，請確定任何產生的金鑰大小不小於提供者的最小值。

> [!NOTE]
> 384位 RSA 已經被視為不安全（如同512位 RSA）。 新式建議（例如[NIST 特殊發行集800-57 第1部分修訂 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)）會建議2048位做為新產生之金鑰的最小大小。

#### <a name="category"></a>分類

密碼編譯

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
