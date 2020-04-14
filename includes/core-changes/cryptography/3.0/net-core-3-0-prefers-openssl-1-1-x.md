---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275129"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET 核心 3.0 更喜歡 OpenSSL 1.1.x 到 OpenSSL 1.0.x

Linux 的 .NET Core 可跨多個 Linux 發行版工作,可以同時支援 OpenSSL 1.0.x 和 OpenSSL 1.1.x。  .NET 核心 2.1 和 .NET Core 2.2 先查找 1.0.x,然後回落至 1.1.x;.NET Core 3.0 先查找 1.1.x。 進行此更改是為了增加對新加密標準的支援。

此更改可能會影響使用 .NET Core 中特定於 OpenSSL 的互通類型的庫或應用程式。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和早期版本中,運行時更喜歡將 OpenSSL 1.0.x 載入到 1.1.x 以上。 這意味著使用 OpenSSL 的<xref:System.IntPtr>互<xref:System.Runtime.InteropServices.SafeHandle>通 和 類型與 libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.so.1.0 / libcrypto.so.so.10 按首選項使用。

從 .NET Core 3.0 開始,運行時更喜歡載入 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x,因此使用 OpenSSL 的互通<xref:System.IntPtr>和<xref:System.Runtime.InteropServices.SafeHandle>類型與 libcrypto.so.so.1.1/ libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1.1.1 首選項一起使用。 因此,當從 .NET Core 2.1 或 .NET Core 2.2 升級時,直接與 OpenSSL 互通的庫和應用程式可能具有與 .NET Core 公開值不相容的指標。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

使用 OpenSSL 直接操作的庫和應用程式需要小心,以確保它們使用與 .NET Core 運行時相同的 OpenSSL 版本。

使用 .NET<xref:System.IntPtr>Core 加密<xref:System.Runtime.InteropServices.SafeHandle>類型或直接使用 OpenSSL 的值的所有庫或應用程式都應<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>將其使用的庫版本與新 屬性進行比較,以確保指標相容。

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
