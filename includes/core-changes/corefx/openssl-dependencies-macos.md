---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032024"
---
### <a name="openssl-versions-on-macos"></a>MacOS 上的 OpenSSL 版本

MacOS 上的 .net Core 3.0 和更新版本執行時間現在會偏好 OpenSSL 1.1. x 版，以針對、、 <xref:System.Security.Cryptography.AesCcm> 、、、 <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 和 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型 OpenSSL 1.0. x 版。

.NET Core 2.1 執行時間現在支援 OpenSSL 1.1. x 版，但仍優先于 OpenSSL 1.0. x 版本。

#### <a name="change-description"></a>變更描述

先前，.NET Core 執行時間在 macOS 上使用 OpenSSL 1.0. x 版的型別與 OpenSSL 互動。 最新的 OpenSSL 1.0. x 版（OpenSSL 1.0.2）現已不支援。 為了在支援的 OpenSSL 版本上保留使用 OpenSSL 的類型，.NET Core 3.0 和更新版本的執行時間現在會在 macOS 上使用較新版本的 OpenSSL。

透過這項變更，macOS 上的 .NET Core 執行時間行為如下所示：

- .NET Core 3.0 和更新版本執行時間會使用 OpenSSL 1.1. x （如果有的話），而且只有在沒有可用的 1.1. x 版本時，才會切換回 OpenSSL 1.0. x。

  針對使用 OpenSSL interop 型別搭配自訂 P/Invoke 的呼叫端，請依照備註中的指導方針進行 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。 如果您沒有檢查此值，您的應用程式可能會損毀 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> 。

- .NET Core 2.1 執行時間使用 OpenSSL 1.0. x （如果有的話），如果沒有可用的 1.0. x 版本，則會切換回 OpenSSL 1.1. x。

  2.1 執行時間偏好較早的 OpenSSL 版本，因為該 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 屬性不存在於 .Net Core 2.1 中，因此無法在執行時間可靠地判斷 OpenSSL 版本。

#### <a name="version-introduced"></a>引進的版本

- .NET Core 2.1.16
- .NET Core 3.0。3
- .NET Core 3.1。2

#### <a name="recommended-action"></a>建議的動作

- 如果不再需要 OpenSSL 版本1.0.2，請將它卸載。

- 如果您使用 <xref:System.Security.Cryptography.AesCcm> 、、 <xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl> 、 <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> 、、 <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 或 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型，請安裝 OpenSSL 1.1. x。

- 如果您搭配自訂 P/Invoke 使用 OpenSSL interop 類型，請遵循備註中的指引 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
