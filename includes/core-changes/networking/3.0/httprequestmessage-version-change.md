---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451876"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="4f859-101">HttpRequestMessage 的預設值已變更為1。1</span><span class="sxs-lookup"><span data-stu-id="4f859-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="4f859-102">屬性的預設值 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 已從2.0 變更為1.1。</span><span class="sxs-lookup"><span data-stu-id="4f859-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4f859-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4f859-103">Version introduced</span></span>

<span data-ttu-id="4f859-104">3.0</span><span class="sxs-lookup"><span data-stu-id="4f859-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="4f859-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="4f859-105">Change description</span></span>

<span data-ttu-id="4f859-106">在 .NET Core 1.0 至2.0 中，屬性的預設值 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 為1.1。</span><span class="sxs-lookup"><span data-stu-id="4f859-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="4f859-107">從 .NET Core 2.1 開始，它已變更為2.1。</span><span class="sxs-lookup"><span data-stu-id="4f859-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="4f859-108">從 .NET Core 3.0 開始，屬性傳回的預設版本號碼 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 會再次1.1。</span><span class="sxs-lookup"><span data-stu-id="4f859-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4f859-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4f859-109">Recommended action</span></span>

<span data-ttu-id="4f859-110">如果您的程式碼相依于傳回預設值2.0 的屬性，請更新您的程式碼 <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="4f859-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="4f859-111">類別</span><span class="sxs-lookup"><span data-stu-id="4f859-111">Category</span></span>

<span data-ttu-id="4f859-112">網路功能</span><span class="sxs-lookup"><span data-stu-id="4f859-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4f859-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4f859-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
