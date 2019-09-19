---
ms.openlocfilehash: 07ab65de16b72bd0844a39e4b35235c5f043f3ec
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117245"
---
### <a name="minimum-size-for-rsaopenssl-key-generation-has-increased"></a><span data-ttu-id="0a49d-101">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="0a49d-101">Minimum size for RSAOpenSsl key generation has increased</span></span>

<span data-ttu-id="0a49d-102">在 Linux 上產生新 RSA 金鑰的最小大小已從 384-位增加至512位。</span><span class="sxs-lookup"><span data-stu-id="0a49d-102">The minimum size for generating new RSA keys on Linux has increased from 384-bit to 512-bit.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0a49d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0a49d-103">Change description</span></span>

<span data-ttu-id="0a49d-104">從 .net Core 3.0 開始，從 < 系統的 rsa 實例上的`LegalKeySizes`屬性所報告的最小合法金鑰大小。 RSAOpenSsl. Create% 2a？ displayProperty = namewithtype> >，< system.object。23ctor% 2A？ displayProperty = Namewithtype> >，而 < 系統. RSACryptoServicePlatform.% 23ctor% 2A？ displayProperty = Namewithtype> > on Linux 已從384增加至512。</span><span class="sxs-lookup"><span data-stu-id="0a49d-104">Starting with .NET Core 3.0, the minimum legal key size reported by the `LegalKeySizes` property on RSA instances from <System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, <System.Security.Cryptography.RSAOpenSsl.%23ctor%2A?displayProperty=nameWithType>, and <System.Security.Cryptography.RSACryptoServicePlatform.%23ctor%2A?displayProperty=nameWithType> on Linux has increased from 384 to 512.</span></span>

<span data-ttu-id="0a49d-105">因此，在 .net Core 2.2 和更早版本中，方法呼叫（例如`RSA.Create(384)` ）會成功。</span><span class="sxs-lookup"><span data-stu-id="0a49d-105">As a result, in .NET Core 2.2 and earlier versions, a method call such as `RSA.Create(384)` succeeds.</span></span> <span data-ttu-id="0a49d-106">在 .net Core 3.0 和更新版本中，方法呼叫`RSA.Create(384)`會擲回例外狀況，指出大小太小。</span><span class="sxs-lookup"><span data-stu-id="0a49d-106">In .NET Core 3.0 and later versions, the method call `RSA.Create(384)` throws an exception indicating the size is too small.</span></span>

<span data-ttu-id="0a49d-107">已進行此變更，因為 OpenSSL 會在 Linux 上執行密碼編譯作業，並在版本1.0.2 和1.1.0 之間產生最小值。</span><span class="sxs-lookup"><span data-stu-id="0a49d-107">This changes was made because OpenSSL, which performs the cryptographic operations on Linux, raised its minimum between versions 1.0.2 and 1.1.0.</span></span>  <span data-ttu-id="0a49d-108">.NET Core 3.0 傾向于將 OpenSSL 1.1. x 新增至 1.0. x，並產生最小的回報版本，以反映這項較高的相依性限制。</span><span class="sxs-lookup"><span data-stu-id="0a49d-108">.NET Core 3.0 prefers OpenSSL 1.1.x to 1.0.x, and the minimum reported version was raised to reflect this new higher dependency limitation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0a49d-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0a49d-109">Version introduced</span></span>

<span data-ttu-id="0a49d-110">3.0</span><span class="sxs-lookup"><span data-stu-id="0a49d-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a49d-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0a49d-111">Recommended action</span></span>

<span data-ttu-id="0a49d-112">如果您呼叫任何受影響的 Api，請確定任何產生的金鑰大小不小於提供者的最小值。</span><span class="sxs-lookup"><span data-stu-id="0a49d-112">If you call any of the affected APIs, ensure that the size of any generated keys is not less than the provider minimum.</span></span>

> [!NOTE]
> <span data-ttu-id="0a49d-113">384位 RSA 已經被視為不安全（如同512位 RSA）。</span><span class="sxs-lookup"><span data-stu-id="0a49d-113">384-bit RSA is already considered insecure (as is 512-bit RSA).</span></span> <span data-ttu-id="0a49d-114">新式建議（例如[NIST 特殊發行集800-57 第1部分修訂 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf)）會建議2048位做為新產生之金鑰的最小大小。</span><span class="sxs-lookup"><span data-stu-id="0a49d-114">Modern recommendations, such as [NIST Special Publication 800-57 Part 1 Revision 4](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r4.pdf), suggest 2048-bit as the minimum size for newly generated keys.</span></span>

#### <a name="category"></a><span data-ttu-id="0a49d-115">分類</span><span class="sxs-lookup"><span data-stu-id="0a49d-115">Category</span></span>

<span data-ttu-id="0a49d-116">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="0a49d-116">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a49d-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0a49d-117">Affected APIs</span></span>

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
