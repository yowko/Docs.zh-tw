---
ms.openlocfilehash: 6a5cd260a2820e2a81142f6d55e32e91173ca503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147447"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="b4028-101">macOS 上的打開 SSL 版本</span><span class="sxs-lookup"><span data-stu-id="b4028-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="b4028-102">在 macOS 上 .NET Core 3.0 和更高版本的運行時現在首選 OpenSSL 1.1.x 版本，而<xref:System.Security.Cryptography.AesCcm>對於<xref:System.Security.Cryptography.AesGcm> <xref:System.Security.Cryptography.DSAOpenSsl>、、、、、、、、、、、<xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl><xref:System.Security.Cryptography.ECDsaOpenSsl><xref:System.Security.Cryptography.RSAOpenSsl>和<xref:System.Security.Cryptography.SafeEvpPKeyHandle>類型，則首選 OpenSSL 1.0.x 版本。</span><span class="sxs-lookup"><span data-stu-id="b4028-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="b4028-103">.NET Core 2.1 運行時現在支援 OpenSSL 1.1.x 版本，但仍喜歡 OpenSSL 1.0.x 版本。</span><span class="sxs-lookup"><span data-stu-id="b4028-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b4028-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="b4028-104">Change description</span></span>

<span data-ttu-id="b4028-105">以前，.NET 核心運行時在 macOS 上使用 OpenSSL 1.0.x 版本，用於與 OpenSSL 交互的類型。</span><span class="sxs-lookup"><span data-stu-id="b4028-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="b4028-106">最新的 OpenSSL 1.0.x 版本 OpenSSL 1.0.2 現已退出支援。</span><span class="sxs-lookup"><span data-stu-id="b4028-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="b4028-107">為了保持在受支援的 OpenSSL 版本上使用 OpenSSL 的類型，.NET Core 3.0 及更高版本的運行時現在在 macOS 上使用較新版本的 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="b4028-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="b4028-108">通過此更改，macOS 上的 .NET Core 運行時的行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="b4028-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="b4028-109">.NET Core 3.0 及更高版本運行時使用 OpenSSL 1.1.x（如果可用），並且僅在沒有 1.1.x 版本可用時才回落到 OpenSSL 1.0.x。</span><span class="sxs-lookup"><span data-stu-id="b4028-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="b4028-110">對於使用 OpenSSL 與自訂 P/Invokes 一起使用 OpenSSL 交互操作<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>類型的調用方，請按照備註中的指南操作。</span><span class="sxs-lookup"><span data-stu-id="b4028-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="b4028-111">如果不檢查該值，<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion>你的應用可能會崩潰。</span><span class="sxs-lookup"><span data-stu-id="b4028-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="b4028-112">.NET Core 2.1 運行時使用 OpenSSL 1.0.x（如果可用），如果沒有可用的 1.0.x 版本，則回退到 OpenSSL 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="b4028-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="b4028-113">2.1 運行時更喜歡早期版本的 OpenSSL，因為<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>屬性不存在於 .NET Core 2.1 中，因此無法在運行時可靠地確定 OpenSSL 版本。</span><span class="sxs-lookup"><span data-stu-id="b4028-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b4028-114">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="b4028-114">Version introduced</span></span>

- <span data-ttu-id="b4028-115">.NET 核心 2.1.16</span><span class="sxs-lookup"><span data-stu-id="b4028-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="b4028-116">.NET 核心 3.0.3</span><span class="sxs-lookup"><span data-stu-id="b4028-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="b4028-117">.NET 核心 3.1.2</span><span class="sxs-lookup"><span data-stu-id="b4028-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b4028-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b4028-118">Recommended action</span></span>

- <span data-ttu-id="b4028-119">如果不再需要 OpenSSL 版本 1.0.2，請卸載它。</span><span class="sxs-lookup"><span data-stu-id="b4028-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="b4028-120"><xref:System.Security.Cryptography.AesCcm>如果使用<xref:System.Security.Cryptography.AesGcm>、、、、、、、<xref:System.Security.Cryptography.DSAOpenSsl><xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl><xref:System.Security.Cryptography.ECDsaOpenSsl><xref:System.Security.Cryptography.RSAOpenSsl>或<xref:System.Security.Cryptography.SafeEvpPKeyHandle>類型，請安裝 OpenSSL 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="b4028-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="b4028-121">如果將 OpenSSL 互通類型與自訂 P/Invokes 一起使用，請<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>按照備註中的指南操作。</span><span class="sxs-lookup"><span data-stu-id="b4028-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="b4028-122">類別</span><span class="sxs-lookup"><span data-stu-id="b4028-122">Category</span></span>

<span data-ttu-id="b4028-123">CoreFx</span><span class="sxs-lookup"><span data-stu-id="b4028-123">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b4028-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b4028-124">Affected APIs</span></span>

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
