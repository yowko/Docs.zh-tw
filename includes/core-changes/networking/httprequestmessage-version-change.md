---
ms.openlocfilehash: 78d2ec6fb505573ad36d55a9ca0a20452b7fa244
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002886"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="acde7-101">HttpRequestMessage 的預設值。版本已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="acde7-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span> 

<span data-ttu-id="acde7-102">@No__t-0 屬性的預設值已從2.0 變更為1.1。</span><span class="sxs-lookup"><span data-stu-id="acde7-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="acde7-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="acde7-103">Version introduced</span></span>

<span data-ttu-id="acde7-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="acde7-104">.NET Core 3.0</span></span>

#### <a name="details"></a><span data-ttu-id="acde7-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="acde7-105">Details</span></span>

<span data-ttu-id="acde7-106">在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。</span><span class="sxs-lookup"><span data-stu-id="acde7-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="acde7-107">從 .NET Core 2.1 開始，它已變更為2.1。</span><span class="sxs-lookup"><span data-stu-id="acde7-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span> 

<span data-ttu-id="acde7-108">從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。</span><span class="sxs-lookup"><span data-stu-id="acde7-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="acde7-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="acde7-109">Recommended action</span></span>

<span data-ttu-id="acde7-110">如果您的程式碼相依于 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性，則會傳回預設值2.0。</span><span class="sxs-lookup"><span data-stu-id="acde7-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="acde7-111">Category</span><span class="sxs-lookup"><span data-stu-id="acde7-111">Category</span></span>

<span data-ttu-id="acde7-112">網路</span><span class="sxs-lookup"><span data-stu-id="acde7-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="acde7-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="acde7-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

