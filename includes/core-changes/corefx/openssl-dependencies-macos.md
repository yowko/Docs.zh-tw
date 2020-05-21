---
ms.openlocfilehash: a4476fbff572c004632153e5a98812c241efca57
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721213"
---
### <a name="openssl-versions-on-macos"></a><span data-ttu-id="06f41-101">MacOS 上的 OpenSSL 版本</span><span class="sxs-lookup"><span data-stu-id="06f41-101">OpenSSL versions on macOS</span></span>

<span data-ttu-id="06f41-102">MacOS 上的 .net Core 3.0 和更新版本執行時間現在偏好 OpenSSL 1.1. x 版，以 OpenSSL <xref:System.Security.Cryptography.AesCcm> 、 <xref:System.Security.Cryptography.AesGcm> 、、、、 <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 和 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型的1.0 版。</span><span class="sxs-lookup"><span data-stu-id="06f41-102">The .NET Core 3.0 and later runtimes on macOS now prefer OpenSSL 1.1.x versions to OpenSSL 1.0.x versions for the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, and <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

<span data-ttu-id="06f41-103">.NET Core 2.1 執行時間現在支援 OpenSSL 1.1. x 版，但仍優先于 OpenSSL 1.0. x 版。</span><span class="sxs-lookup"><span data-stu-id="06f41-103">The .NET Core 2.1 runtime now supports OpenSSL 1.1.x versions, but still prefers OpenSSL 1.0.x versions.</span></span>

#### <a name="change-description"></a><span data-ttu-id="06f41-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="06f41-104">Change description</span></span>

<span data-ttu-id="06f41-105">之前，.NET Core 執行時間會針對與 OpenSSL 互動的類型，在 macOS 上使用 OpenSSL 1.0. x 版。</span><span class="sxs-lookup"><span data-stu-id="06f41-105">Previously, the .NET Core runtime used OpenSSL 1.0.x versions on macOS for types that interact with OpenSSL.</span></span> <span data-ttu-id="06f41-106">最新的 OpenSSL 1.0. x 版 OpenSSL 1.0.2 現在不支援。</span><span class="sxs-lookup"><span data-stu-id="06f41-106">The most recent OpenSSL 1.0.x version, OpenSSL 1.0.2, is now out of support.</span></span> <span data-ttu-id="06f41-107">若要保留在支援的 OpenSSL 版本上使用 OpenSSL 的類型，.NET Core 3.0 和更新版本的執行時間現在會在 macOS 上使用較新版的 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="06f41-107">To keep types that use OpenSSL on supported versions of OpenSSL, the .NET Core 3.0 and later runtimes now use newer versions of OpenSSL on macOS.</span></span>

<span data-ttu-id="06f41-108">透過這種變更，macOS 上 .NET Core 執行時間的行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="06f41-108">With this change, the behavior for the .NET Core runtimes on macOS is as follows:</span></span>

- <span data-ttu-id="06f41-109">.NET Core 3.0 和更新版本執行時間會使用 OpenSSL 1.1. x （如果有的話），而且只有在沒有 1.1. x 版的情況下，才會切換回 OpenSSL 1.0. x。</span><span class="sxs-lookup"><span data-stu-id="06f41-109">The .NET Core 3.0 and later version runtimes use OpenSSL 1.1.x, if available, and fall back to OpenSSL 1.0.x only if there's no 1.1.x version available.</span></span>

  <span data-ttu-id="06f41-110">針對搭配使用 OpenSSL interop 類型與自訂 P/Invoke 的呼叫端，請遵循備註中的指導方針 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="06f41-110">For callers that use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span> <span data-ttu-id="06f41-111">如果您未檢查此值，您的應用程式可能會損毀 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> 。</span><span class="sxs-lookup"><span data-stu-id="06f41-111">Your app may crash if you don't check the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion> value.</span></span>

- <span data-ttu-id="06f41-112">.NET Core 2.1 執行時間會使用 OpenSSL 1.0. x （如果有的話），並在沒有可用的 1.0. x 版時，切換回 OpenSSL 1.1. x。</span><span class="sxs-lookup"><span data-stu-id="06f41-112">The .NET Core 2.1 runtime uses OpenSSL 1.0.x, if available, and falls back to OpenSSL 1.1.x if there's no 1.0.x version available.</span></span>

  <span data-ttu-id="06f41-113">2.1 執行時間偏好舊版的 OpenSSL，因為屬性不 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 存在於 .Net Core 2.1 中，因此無法在執行時間可靠地判斷 OpenSSL 版本。</span><span class="sxs-lookup"><span data-stu-id="06f41-113">The 2.1 runtime prefers the earlier version of OpenSSL because the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property does not exist in .NET Core 2.1, so the OpenSSL version cannot be reliably determined at run time.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06f41-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="06f41-114">Version introduced</span></span>

- <span data-ttu-id="06f41-115">.NET Core 2.1.16</span><span class="sxs-lookup"><span data-stu-id="06f41-115">.NET Core 2.1.16</span></span>
- <span data-ttu-id="06f41-116">.NET Core 3.0。3</span><span class="sxs-lookup"><span data-stu-id="06f41-116">.NET Core 3.0.3</span></span>
- <span data-ttu-id="06f41-117">.NET Core 3.1。2</span><span class="sxs-lookup"><span data-stu-id="06f41-117">.NET Core 3.1.2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06f41-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="06f41-118">Recommended action</span></span>

- <span data-ttu-id="06f41-119">如果不再需要 OpenSSL 版本1.0.2，請將其卸載。</span><span class="sxs-lookup"><span data-stu-id="06f41-119">Uninstall OpenSSL version 1.0.2 if it's no longer needed.</span></span>

- <span data-ttu-id="06f41-120">如果您使用 <xref:System.Security.Cryptography.AesCcm> 、 <xref:System.Security.Cryptography.AesGcm> 、、、、 <xref:System.Security.Cryptography.DSAOpenSsl> <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl> <xref:System.Security.Cryptography.ECDsaOpenSsl> <xref:System.Security.Cryptography.RSAOpenSsl> 或 <xref:System.Security.Cryptography.SafeEvpPKeyHandle> 類型，請安裝 OpenSSL 1.1. x。</span><span class="sxs-lookup"><span data-stu-id="06f41-120">Install OpenSSL 1.1.x if you use the <xref:System.Security.Cryptography.AesCcm>, <xref:System.Security.Cryptography.AesGcm>, <xref:System.Security.Cryptography.DSAOpenSsl>, <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl>, <xref:System.Security.Cryptography.ECDsaOpenSsl>, <xref:System.Security.Cryptography.RSAOpenSsl>, or <xref:System.Security.Cryptography.SafeEvpPKeyHandle> types.</span></span>

- <span data-ttu-id="06f41-121">如果您搭配使用 OpenSSL interop 類型與自訂 P/Invoke，請遵循備註中的指引 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="06f41-121">If you use the OpenSSL interop types with custom P/Invokes, follow the guidance in the <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> remarks.</span></span>

#### <a name="category"></a><span data-ttu-id="06f41-122">類別</span><span class="sxs-lookup"><span data-stu-id="06f41-122">Category</span></span>

<span data-ttu-id="06f41-123">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="06f41-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06f41-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="06f41-124">Affected APIs</span></span>

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
