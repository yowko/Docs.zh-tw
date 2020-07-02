---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614586"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="1326a-101">WPF PackageDigitalSignatureManager 的預設雜湊演算法現在是 SHA256</span><span class="sxs-lookup"><span data-stu-id="1326a-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="1326a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1326a-102">Details</span></span>

<span data-ttu-id="1326a-103">`System.IO.Packaging.PackageDigitalSignatureManager` 提供與 WPF 套件相關的數位簽章功能。</span><span class="sxs-lookup"><span data-stu-id="1326a-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="1326a-104">在 .NET Framework 4.7 和舊版中，用來簽署套件各部分的預設演算法 (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) 是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="1326a-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="1326a-105">由於最新的 SHA1 安全性考量之故，這個預設值從 .NET Framework 4.7.1 開始已變更為 SHA256。</span><span class="sxs-lookup"><span data-stu-id="1326a-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="1326a-106">這項變更會影響所有套件簽署，包括 XPS 文件。</span><span class="sxs-lookup"><span data-stu-id="1326a-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1326a-107">建議</span><span class="sxs-lookup"><span data-stu-id="1326a-107">Suggestion</span></span>

<span data-ttu-id="1326a-108">開發人員若想要在目標設為低於 .NET Framework 4.7.1 的 Framework 版本時利用這項變更，或在目標設為 .NET Framework 4.7.1 或更高版本時使用先前的功能，可以適當地設定下列 AppContext 旗標。</span><span class="sxs-lookup"><span data-stu-id="1326a-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="1326a-109">true 值會導致使用 SHA1 作為預設演算法；false 值則導致使用 SHA256。</span><span class="sxs-lookup"><span data-stu-id="1326a-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1326a-110">名稱</span><span class="sxs-lookup"><span data-stu-id="1326a-110">Name</span></span>    | <span data-ttu-id="1326a-111">值</span><span class="sxs-lookup"><span data-stu-id="1326a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1326a-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="1326a-112">Scope</span></span>   | <span data-ttu-id="1326a-113">Edge</span><span class="sxs-lookup"><span data-stu-id="1326a-113">Edge</span></span>        |
| <span data-ttu-id="1326a-114">版本</span><span class="sxs-lookup"><span data-stu-id="1326a-114">Version</span></span> | <span data-ttu-id="1326a-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="1326a-115">4.7.1</span></span>       |
| <span data-ttu-id="1326a-116">類型</span><span class="sxs-lookup"><span data-stu-id="1326a-116">Type</span></span>    | <span data-ttu-id="1326a-117">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="1326a-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1326a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1326a-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>
