---
ms.openlocfilehash: b5b724afefcce69df706f2bea0b1612db653af03
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275526"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="21683-101">RSAOpenSsl 金鑰產生的最低大小已增加</span><span class="sxs-lookup"><span data-stu-id="21683-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="21683-102">在 Linux 上生成新 RSA 金鑰的最小大小從 384 位元增加到 512 位元。</span><span class="sxs-lookup"><span data-stu-id="21683-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="21683-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="21683-103">Change description</span></span>

<span data-ttu-id="21683-104">從 .NET Core`LegalKeySizes`3.0 開始,屬性在 RSA 實<xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>例上<xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>報告的<xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>最小法律 密鑰 大小從 、和 Linux 上從 384 增加到 512。</span><span class="sxs-lookup"><span data-stu-id="21683-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>, and <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="21683-105">因此,在 .NET Core 2.2 和早期版本中,`RSA.Create(384)`方法調用( 如成功)將成功。</span><span class="sxs-lookup"><span data-stu-id="21683-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="21683-106">在 .NET Core 3.0`RSA.Create(384)`和更高版本中 ,方法調用將引發一個異常,指示大小太小。</span><span class="sxs-lookup"><span data-stu-id="21683-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="21683-107">之所以做出此更改,是因為在 Linux 上執行加密操作的 OpenSSL 在版本 1.0.2 和 1.1.0 之間提高了最小值。</span><span class="sxs-lookup"><span data-stu-id="21683-107">This change was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span> <span data-ttu-id="21683-108">.NET Core 3.0 更喜歡 OpenSSL 1.1.x 到 1.0.x,並且提出了最低報告版本以反映這種新的更高依賴項限制。</span><span class="sxs-lookup"><span data-stu-id="21683-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="21683-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="21683-109">Version introduced</span></span>

<span data-ttu-id="21683-110">3.0</span><span class="sxs-lookup"><span data-stu-id="21683-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="21683-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="21683-111">Recommended action</span></span>

<span data-ttu-id="21683-112">如果調用任何受影響的 API,請確保任何生成的密鑰的大小不小於提供程式的最小值。</span><span class="sxs-lookup"><span data-stu-id="21683-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="21683-113">384 位 RSA 已被視為不安全(如 512 位 RSA)。</span><span class="sxs-lookup"><span data-stu-id="21683-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="21683-114">現代建議,如[NIST 特別出版物 800-57 第 1 部分修訂版 4,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)建議將 2048 位作為新生成的密鑰的最小大小。</span><span class="sxs-lookup"><span data-stu-id="21683-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="21683-115">類別</span><span class="sxs-lookup"><span data-stu-id="21683-115">Category</span></span>

<span data-ttu-id="21683-116">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="21683-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21683-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="21683-117">Affected APIs</span></span>

- <xref:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor%2A>
- <xref:System.Security.Cryptography.RSACryptoServiceProvider.%23ctor%2A>

<!--
### Affected APIs

- `P:System.Security.Cryptography.AsymmetricAlgorithm.LegalKeySizes`
- `Overload:System.Security.Cryptography.RSA.Create`
- `Overload:System.Security.Cryptography.RSAOpenSsl.#ctor`
- `Overload:System.Security.Cryptography.RSACryptoServiceProvider.#ctor`

-->
