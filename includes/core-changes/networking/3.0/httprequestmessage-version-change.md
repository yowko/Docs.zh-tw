---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451876"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="59962-101">HTTPRequestMessage.Version 的預設值更改為 1.1</span><span class="sxs-lookup"><span data-stu-id="59962-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="59962-102">屬性的<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>預設值從 2.0 更改為 1.1。</span><span class="sxs-lookup"><span data-stu-id="59962-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59962-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="59962-103">Version introduced</span></span>

<span data-ttu-id="59962-104">3.0</span><span class="sxs-lookup"><span data-stu-id="59962-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="59962-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="59962-105">Change description</span></span>

<span data-ttu-id="59962-106">在 .NET Core 1.0 到 2.0<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>中，該屬性的預設值為 1.1。</span><span class="sxs-lookup"><span data-stu-id="59962-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="59962-107">從 .NET 核心 2.1 開始，它更改為 2.1。</span><span class="sxs-lookup"><span data-stu-id="59962-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="59962-108">從 .NET Core 3.0 開始，屬性返回的<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>預設版本號再次為 1.1。</span><span class="sxs-lookup"><span data-stu-id="59962-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59962-109">建議的動作</span><span class="sxs-lookup"><span data-stu-id="59962-109">Recommended action</span></span>

<span data-ttu-id="59962-110">如果代碼依賴于返回預設值 2.0 的屬性，<xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>則更新代碼。</span><span class="sxs-lookup"><span data-stu-id="59962-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="59962-111">類別</span><span class="sxs-lookup"><span data-stu-id="59962-111">Category</span></span>

<span data-ttu-id="59962-112">網路功能</span><span class="sxs-lookup"><span data-stu-id="59962-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59962-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="59962-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
