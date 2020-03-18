---
ms.openlocfilehash: 2fb980c8b75e25ba347c56ccc1c90f2959e83e21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568000"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="116b9-101">RSAOpenSsl 金鑰生成的最低大小已增加</span><span class="sxs-lookup"><span data-stu-id="116b9-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="116b9-102">在 Linux 上生成新 RSA 金鑰的最小大小從 384 位增加到 512 位。</span><span class="sxs-lookup"><span data-stu-id="116b9-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="116b9-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="116b9-103">Change description</span></span>

<span data-ttu-id="116b9-104">從 .NET Core 3.0`LegalKeySizes`開始，屬性在 RSA 實例上報告的最小法律<xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>金鑰<xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>大小從<xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType>、和 Linux 上從 384 增加到 512。</span><span class="sxs-lookup"><span data-stu-id="116b9-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="116b9-105">因此，在 .NET Core 2.2 和早期版本中，方法調用（`RSA.Create(384)`如成功）將成功。</span><span class="sxs-lookup"><span data-stu-id="116b9-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="116b9-106">在 .NET Core 3.0 和更高版本中`RSA.Create(384)`，方法調用將引發一個異常，指示大小太小。</span><span class="sxs-lookup"><span data-stu-id="116b9-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="116b9-107">之所以做出此更改，是因為在 Linux 上執行加密操作的 OpenSSL 在版本 1.0.2 和 1.1.0 之間提高了最小值。</span><span class="sxs-lookup"><span data-stu-id="116b9-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="116b9-108">.NET Core 3.0 更喜歡 OpenSSL 1.1.x 到 1.0.x，並且提出了最低報告版本以反映這種新的更高依賴項限制。</span><span class="sxs-lookup"><span data-stu-id="116b9-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="116b9-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="116b9-109">Version introduced</span></span>

<span data-ttu-id="116b9-110">3.0</span><span class="sxs-lookup"><span data-stu-id="116b9-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="116b9-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="116b9-111">Recommended action</span></span>

<span data-ttu-id="116b9-112">如果調用任何受影響的 API，請確保任何生成的金鑰的大小不小於提供程式的最小值。</span><span class="sxs-lookup"><span data-stu-id="116b9-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="116b9-113">384 位 RSA 已被視為不安全（如 512 位 RSA）。</span><span class="sxs-lookup"><span data-stu-id="116b9-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="116b9-114">現代建議，如[NIST 特別出版物 800-57 第 1 部分修訂版 4，](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)建議將 2048 位作為新生成的金鑰的最小大小。</span><span class="sxs-lookup"><span data-stu-id="116b9-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="116b9-115">類別</span><span class="sxs-lookup"><span data-stu-id="116b9-115">Category</span></span>

<span data-ttu-id="116b9-116">Cryptography</span><span class="sxs-lookup"><span data-stu-id="116b9-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="116b9-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="116b9-117">Affected APIs</span></span>

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
