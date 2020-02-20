---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451876"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="14e4a-101">HttpRequestMessage 的預設值。版本已變更為1.1</span><span class="sxs-lookup"><span data-stu-id="14e4a-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="14e4a-102"><xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值已從2.0 變更為1.1。</span><span class="sxs-lookup"><span data-stu-id="14e4a-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14e4a-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="14e4a-103">Version introduced</span></span>

<span data-ttu-id="14e4a-104">3.0</span><span class="sxs-lookup"><span data-stu-id="14e4a-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="14e4a-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="14e4a-105">Change description</span></span>

<span data-ttu-id="14e4a-106">在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。</span><span class="sxs-lookup"><span data-stu-id="14e4a-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="14e4a-107">從 .NET Core 2.1 開始，它已變更為2.1。</span><span class="sxs-lookup"><span data-stu-id="14e4a-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="14e4a-108">從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。</span><span class="sxs-lookup"><span data-stu-id="14e4a-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="14e4a-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="14e4a-109">Recommended action</span></span>

<span data-ttu-id="14e4a-110">更新您的程式碼（如果它相依于傳回預設值2.0 的 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性）。</span><span class="sxs-lookup"><span data-stu-id="14e4a-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="14e4a-111">類別</span><span class="sxs-lookup"><span data-stu-id="14e4a-111">Category</span></span>

<span data-ttu-id="14e4a-112">網路功能</span><span class="sxs-lookup"><span data-stu-id="14e4a-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14e4a-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="14e4a-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
