---
ms.openlocfilehash: 65d8ca480d41a3807473583355fe8be41e0e9701
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275129"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="8db54-101">.NET 核心 3.0 更喜歡 OpenSSL 1.1.x 到 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="8db54-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="8db54-102">Linux 的 .NET Core 可跨多個 Linux 發行版工作,可以同時支援 OpenSSL 1.0.x 和 OpenSSL 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="8db54-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="8db54-103">.NET 核心 2.1 和 .NET Core 2.2 先查找 1.0.x,然後回落至 1.1.x;.NET Core 3.0 先查找 1.1.x。</span><span class="sxs-lookup"><span data-stu-id="8db54-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="8db54-104">進行此更改是為了增加對新加密標準的支援。</span><span class="sxs-lookup"><span data-stu-id="8db54-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="8db54-105">此更改可能會影響使用 .NET Core 中特定於 OpenSSL 的互通類型的庫或應用程式。</span><span class="sxs-lookup"><span data-stu-id="8db54-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8db54-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="8db54-106">Change description</span></span>

<span data-ttu-id="8db54-107">在 .NET Core 2.2 和早期版本中,運行時更喜歡將 OpenSSL 1.0.x 載入到 1.1.x 以上。</span><span class="sxs-lookup"><span data-stu-id="8db54-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="8db54-108">這意味著使用 OpenSSL 的<xref:System.IntPtr>互<xref:System.Runtime.InteropServices.SafeHandle>通 和 類型與 libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.so.1.0 / libcrypto.so.so.10 按首選項使用。</span><span class="sxs-lookup"><span data-stu-id="8db54-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="8db54-109">從 .NET Core 3.0 開始,運行時更喜歡載入 OpenSSL 1.1.x 而不是 OpenSSL 1.0.x,因此使用 OpenSSL 的互通<xref:System.IntPtr>和<xref:System.Runtime.InteropServices.SafeHandle>類型與 libcrypto.so.so.1.1/ libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1.1.1 首選項一起使用。</span><span class="sxs-lookup"><span data-stu-id="8db54-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="8db54-110">因此,當從 .NET Core 2.1 或 .NET Core 2.2 升級時,直接與 OpenSSL 互通的庫和應用程式可能具有與 .NET Core 公開值不相容的指標。</span><span class="sxs-lookup"><span data-stu-id="8db54-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8db54-111">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="8db54-111">Version introduced</span></span>

<span data-ttu-id="8db54-112">3.0</span><span class="sxs-lookup"><span data-stu-id="8db54-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8db54-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8db54-113">Recommended action</span></span>

<span data-ttu-id="8db54-114">使用 OpenSSL 直接操作的庫和應用程式需要小心,以確保它們使用與 .NET Core 運行時相同的 OpenSSL 版本。</span><span class="sxs-lookup"><span data-stu-id="8db54-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="8db54-115">使用 .NET<xref:System.IntPtr>Core 加密<xref:System.Runtime.InteropServices.SafeHandle>類型或直接使用 OpenSSL 的值的所有庫或應用程式都應<xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>將其使用的庫版本與新 屬性進行比較,以確保指標相容。</span><span class="sxs-lookup"><span data-stu-id="8db54-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="8db54-116">類別</span><span class="sxs-lookup"><span data-stu-id="8db54-116">Category</span></span>

<span data-ttu-id="8db54-117">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="8db54-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8db54-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8db54-118">Affected APIs</span></span>

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
