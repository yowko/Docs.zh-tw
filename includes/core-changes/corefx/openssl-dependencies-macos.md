---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147447"
---
### <a name="openssl-versions-on-macos"></a>macOS 上的打開 SSL 版本

在 macOS 上 .NET Core 3.0 和更高版本的運行時現在首選 OpenSSL 1.1.x 版本，而<xref:System.Security.Cryptography.AesCcm>對於<xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>、、、、、、、、、、、<xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl><xref:System.Security.Cryptography.ECDsaOpenSsl><xref:System.Security.Cryptography.RSAOpenSsl>和<xref:System.Security.Cryptography.SafeEvpPKeyHandle>類型，則首選 OpenSSL 1.0.x 版本。

.NET Core 2.1 運行時現在支援 OpenSSL 1.1.x 版本，但仍喜歡 OpenSSL 1.0.x 版本。

#### <a name="change-description"></a>變更描述

以前，.NET 核心運行時在 macOS 上使用 OpenSSL 1.0.x 版本，用於與 OpenSSL 交互的類型。 最新的 OpenSSL 1.0.x 版本 OpenSSL 1.0.2 現已退出支援。 為了保持在受支援的 OpenSSL 版本上使用 OpenSSL 的類型，.NET Core 3.0 及更高版本的運行時現在在 macOS 上使用較新版本的 OpenSSL。

通過此更改，macOS 上的 .NET Core 運行時的行為如下所示：

- .NET Core 3.0 及更高版本運行時使用 OpenSSL 1.1.x（如果可用），並且僅在沒有 1.1.x 版本可用時才回落到 OpenSSL 1.0.x。

  對於使用 OpenSSL 與自訂 P/Invokes 一起使用 OpenSSL 交互操作<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>類型的調用方，請按照備註中的指南操作。 如果不檢查該值，<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion>你的應用可能會崩潰。

- .NET Core 2.1 運行時使用 OpenSSL 1.0.x（如果可用），如果沒有可用的 1.0.x 版本，則回退到 OpenSSL 1.1.x。

  2.1 運行時更喜歡早期版本的 OpenSSL，因為<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>屬性不存在於 .NET Core 2.1 中，因此無法在運行時可靠地確定 OpenSSL 版本。

#### <a name="version-introduced"></a>介紹的版本

- .NET 核心 2.1.16
- .NET 核心 3.0.3
- .NET 核心 3.1.2

#### <a name="recommended-action"></a>建議的動作

- 如果不再需要 OpenSSL 版本 1.0.2，請卸載它。

- <xref:System.Security.Cryptography.AesCcm>如果使用<xref:System.Security.Cryptography.AesGcm>、、、、、、、<xref:System.Security.Cryptography.DSAOpenSsl><xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl><xref:System.Security.Cryptography.ECDsaOpenSsl><xref:System.Security.Cryptography.RSAOpenSsl>或<xref:System.Security.Cryptography.SafeEvpPKeyHandle>類型，請安裝 OpenSSL 1.1.x。

- 如果將 OpenSSL 互通類型與自訂 P/Invokes 一起使用，請<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>按照備註中的指南操作。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.AesCcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.AesGcm?displayProperty=fullName>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.SafeEvpPKeyHandle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.AesCcm``
- `T:System.Security.Cryptography.AesGcm`
- `T:System.Security.Cryptography.DSAOpenSsl`
- `T:System.Security.Cryptography.ECDiffieHellmanOpenSsl`
- `T:System.Security.Cryptography.ECDsaOpenSsl`
- `T:System.Security.Cryptography.RSAOpenSsl`
- `T:System.Security.Cryptography.SafeEvpPKeyHandle`

-->
