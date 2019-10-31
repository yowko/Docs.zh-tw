---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198371"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="ec619-101">HttpRequestMessage 的預設值。版本已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="ec619-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="ec619-102"><xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值已從2.0 變更為1.1。</span><span class="sxs-lookup"><span data-stu-id="ec619-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ec619-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ec619-103">Version introduced</span></span>

<span data-ttu-id="ec619-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ec619-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="ec619-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="ec619-105">Change description</span></span>

<span data-ttu-id="ec619-106">在 .NET Core 1.0 到2.0 中，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性的預設值是1.1。</span><span class="sxs-lookup"><span data-stu-id="ec619-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="ec619-107">從 .NET Core 2.1 開始，它已變更為2.1。</span><span class="sxs-lookup"><span data-stu-id="ec619-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="ec619-108">從 .NET Core 3.0 開始，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性傳回的預設版本號碼再次為1.1。</span><span class="sxs-lookup"><span data-stu-id="ec619-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ec619-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ec619-109">Recommended action</span></span>

<span data-ttu-id="ec619-110">更新您的程式碼（如果它相依于傳回預設值2.0 的 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 屬性）。</span><span class="sxs-lookup"><span data-stu-id="ec619-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="ec619-111">Category</span><span class="sxs-lookup"><span data-stu-id="ec619-111">Category</span></span>

<span data-ttu-id="ec619-112">網路功能</span><span class="sxs-lookup"><span data-stu-id="ec619-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ec619-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ec619-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

