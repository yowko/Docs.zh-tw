---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032353"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="69a3c-101">裝載：標示為已淘汰和已取代的 IHostingEnvironment 和 IApplicationLifetime 類型</span><span class="sxs-lookup"><span data-stu-id="69a3c-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="69a3c-102">引進了新的類型來取代現有 `IHostingEnvironment` 的和 `IApplicationLifetime` 類型。</span><span class="sxs-lookup"><span data-stu-id="69a3c-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="69a3c-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="69a3c-103">Version introduced</span></span>

<span data-ttu-id="69a3c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="69a3c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="69a3c-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="69a3c-105">Old behavior</span></span>

<span data-ttu-id="69a3c-106">和中有兩種不同的 `IHostingEnvironment` 和 `IApplicationLifetime` 類型 `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` 。</span><span class="sxs-lookup"><span data-stu-id="69a3c-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="69a3c-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="69a3c-107">New behavior</span></span>

<span data-ttu-id="69a3c-108">舊型別已標示為已淘汰，並取代為新的類型。</span><span class="sxs-lookup"><span data-stu-id="69a3c-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="69a3c-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="69a3c-109">Reason for change</span></span>

<span data-ttu-id="69a3c-110">當 `Microsoft.Extensions.Hosting` ASP.NET Core 2.1 引進時，會從複製一些類型，例如 `IHostingEnvironment` 和 `IApplicationLifetime` `Microsoft.AspNetCore.Hosting` 。</span><span class="sxs-lookup"><span data-stu-id="69a3c-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="69a3c-111">部分 ASP.NET Core 3.0 變更會導致應用程式同時包含 `Microsoft.Extensions.Hosting` 和 `Microsoft.AspNetCore.Hosting` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="69a3c-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="69a3c-112">當參考兩個命名空間時，使用這些重複的類型會導致「不明確參考」編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="69a3c-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="69a3c-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="69a3c-113">Recommended action</span></span>

<span data-ttu-id="69a3c-114">以新引進的類型取代舊型別的任何使用方式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="69a3c-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="69a3c-115">**過時的類型 (警告) ：**</span><span class="sxs-lookup"><span data-stu-id="69a3c-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="69a3c-116">**新類型：**</span><span class="sxs-lookup"><span data-stu-id="69a3c-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="69a3c-117">新的 `IHostEnvironment` `IsDevelopment` 和 `IsProduction` 擴充方法位於 `Microsoft.Extensions.Hosting` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="69a3c-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="69a3c-118">可能需要將該命名空間新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="69a3c-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="69a3c-119">類別</span><span class="sxs-lookup"><span data-stu-id="69a3c-119">Category</span></span>

<span data-ttu-id="69a3c-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="69a3c-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="69a3c-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="69a3c-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
