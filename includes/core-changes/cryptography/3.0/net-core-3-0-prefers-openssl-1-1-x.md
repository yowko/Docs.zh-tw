---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721223"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a>.NET Core 3.0 傾向于將 OpenSSL 1.1. x OpenSSL 1.0. x

適用于 Linux 的 .NET Core 可跨多個 Linux 發行版本，同時支援 OpenSSL 1.0. x 和 OpenSSL 1.1. x。  .NET Core 2.1 和 .NET Core 2.2 會先尋找 1.0. x，然後回到 1.1. x; .NET Core 3.0 會先尋找 1.1. x。 這是為了新增密碼編譯標準的支援而進行的變更。

這項變更可能會影響使用 .NET Core 中的 OpenSSL 特定 interop 類型執行平臺 interop 的程式庫或應用程式。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和更早版本中，執行時間偏好在 1.1. x 版上載入 OpenSSL 1.0. x。 這表示 <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> 與 OpenSSL 的互通性和類型會搭配 libcrypto 使用。因此，1.0.0/libcrypto. 1.0/libcrypto。因此，請依照喜好設定。

從 .NET Core 3.0 開始，執行時間偏好在 OpenSSL 1.0. x 上載入 OpenSSL 1.1. x，因此與 OpenSSL 互通的 <xref:System.IntPtr> 和 <xref:System.Runtime.InteropServices.SafeHandle> 類型會用於 libcrypto。因此，1.1/libcrypto. 11/libcrypto。因此，請依喜好設定使用 1.1.0/libcrypto。 因此，從 .NET Core 2.1 或 .NET Core 2.2 升級時，直接與 OpenSSL 互通的程式庫和應用程式可能會與 .NET Core 公開的值具有不相容的指標。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

使用 OpenSSL 直接作業的程式庫和應用程式必須謹慎，以確保它們使用與 .NET Core 執行時間相同的 OpenSSL 版本。

所有從 .NET Core 密碼編譯類型使用或值的程式庫或應用程式，都 <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> 應該將其使用的程式庫版本與新的 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 屬性進行比較，以確保指標相容。

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

#### Affected APIs

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
