---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721213"
---
### <a name="openssl-versions-on-macos"></a>MacOS 上的 OpenSSL 版本

MacOS 上的 .net Core 3.0 和更新版本執行時間現在偏好 OpenSSL 1.1. x 版，以 OpenSSL <xref:System.Security.Cryptography.AesCcm> 、 <xref:System.Security.Cryptography.AesGcm> 、、、、 <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 和 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型的1.0 版。

.NET Core 2.1 執行時間現在支援 OpenSSL 1.1. x 版，但仍優先于 OpenSSL 1.0. x 版。

#### <a name="change-description"></a>變更描述

之前，.NET Core 執行時間會針對與 OpenSSL 互動的類型，在 macOS 上使用 OpenSSL 1.0. x 版。 最新的 OpenSSL 1.0. x 版 OpenSSL 1.0.2 現在不支援。 若要保留在支援的 OpenSSL 版本上使用 OpenSSL 的類型，.NET Core 3.0 和更新版本的執行時間現在會在 macOS 上使用較新版的 OpenSSL。

透過這種變更，macOS 上 .NET Core 執行時間的行為如下所示：

- .NET Core 3.0 和更新版本執行時間會使用 OpenSSL 1.1. x （如果有的話），而且只有在沒有 1.1. x 版的情況下，才會切換回 OpenSSL 1.0. x。

  針對搭配使用 OpenSSL interop 類型與自訂 P/Invoke 的呼叫端，請遵循備註中的指導方針 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。 如果您未檢查此值，您的應用程式可能會損毀 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> 。

- .NET Core 2.1 執行時間會使用 OpenSSL 1.0. x （如果有的話），並在沒有可用的 1.0. x 版時，切換回 OpenSSL 1.1. x。

  2.1 執行時間偏好舊版的 OpenSSL，因為屬性不 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 存在於 .Net Core 2.1 中，因此無法在執行時間可靠地判斷 OpenSSL 版本。

#### <a name="version-introduced"></a>引進的版本

- .NET Core 2.1.16
- .NET Core 3.0。3
- .NET Core 3.1。2

#### <a name="recommended-action"></a>建議的動作

- 如果不再需要 OpenSSL 版本1.0.2，請將其卸載。

- 如果您使用 <xref:System.Security.Cryptography.AesCcm> 、 <xref:System.Security.Cryptography.AesGcm> 、、、、 <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 或 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型，請安裝 OpenSSL 1.1. x。

- 如果您搭配使用 OpenSSL interop 類型與自訂 P/Invoke，請遵循備註中的指引 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。

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
