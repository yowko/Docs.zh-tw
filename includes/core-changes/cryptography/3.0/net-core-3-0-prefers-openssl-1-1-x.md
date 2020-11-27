---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721223"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="59f3a-101">.NET Core 3.0 偏好將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="59f3a-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="59f3a-102">適用于 Linux 的 .NET Core （可跨多個 Linux 發行版本運作）可支援 OpenSSL 1.0. x 和 OpenSSL 1.1. x。</span><span class="sxs-lookup"><span data-stu-id="59f3a-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="59f3a-103">.NET Core 2.1 和 .NET Core 2.2 會先尋找 1.0. x，然後切換回 1.1. x; .NET Core 3.0 會先尋找 1.1. x。</span><span class="sxs-lookup"><span data-stu-id="59f3a-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="59f3a-104">這是為了新增密碼編譯標準的支援所做的變更。</span><span class="sxs-lookup"><span data-stu-id="59f3a-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="59f3a-105">這項變更可能會影響使用 .NET Core 中的 OpenSSL 特定 interop 類型進行平臺交互操作的程式庫或應用程式。</span><span class="sxs-lookup"><span data-stu-id="59f3a-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="59f3a-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="59f3a-106">Change description</span></span>

<span data-ttu-id="59f3a-107">在 .NET Core 2.2 及更早版本中，執行時間偏好在 1.1. x 上載入 OpenSSL 1.0. x。</span><span class="sxs-lookup"><span data-stu-id="59f3a-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="59f3a-108">這表示與 <xref:System.IntPtr> OpenSSL 搭配使用的和型別會搭配 <xref:System.Runtime.InteropServices.SafeHandle> libcrypto 使用，因此 1.0.0/libcrypto. 依此類推 1.0/libcrypto。因此，請依喜好設定來進行10。</span><span class="sxs-lookup"><span data-stu-id="59f3a-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="59f3a-109">從 .NET Core 3.0 開始，執行時間會偏好在 OpenSSL 1.0. x 上載入 OpenSSL 1.1. x， <xref:System.IntPtr> 因此 <xref:System.Runtime.InteropServices.SafeHandle> 與 OpenSSL 的 interop 的和類型會搭配 libcrypto 使用。因此，1.1/libcrypto. 依此類推. 11/libcrypto. 1.1.0/libcrypto。因此，請依喜好設定。</span><span class="sxs-lookup"><span data-stu-id="59f3a-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="59f3a-110">因此，從 .NET Core 2.1 或 .NET Core 2.2 升級時，與 OpenSSL 直接交互操作的程式庫和應用程式可能會有與 .NET Core 公開值不相容的指標。</span><span class="sxs-lookup"><span data-stu-id="59f3a-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59f3a-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="59f3a-111">Version introduced</span></span>

<span data-ttu-id="59f3a-112">3.0</span><span class="sxs-lookup"><span data-stu-id="59f3a-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59f3a-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="59f3a-113">Recommended action</span></span>

<span data-ttu-id="59f3a-114">使用 OpenSSL 直接操作的程式庫和應用程式必須小心，以確保它們使用的 OpenSSL 版本與 .NET Core 執行時間相同。</span><span class="sxs-lookup"><span data-stu-id="59f3a-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="59f3a-115">使用或直接使用 OpenSSL 從 .NET Core 密碼編譯類型中之值的所有程式庫或應用程式， <xref:System.IntPtr> <xref:System.Runtime.InteropServices.SafeHandle> 都應該比較其使用的程式庫版本與新的 <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> 屬性，以確保指標相容。</span><span class="sxs-lookup"><span data-stu-id="59f3a-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="59f3a-116">類別</span><span class="sxs-lookup"><span data-stu-id="59f3a-116">Category</span></span>

<span data-ttu-id="59f3a-117">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="59f3a-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59f3a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="59f3a-118">Affected APIs</span></span>

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
