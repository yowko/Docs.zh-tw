---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394056"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="eadab-101">託管：IHosting 環境和 IApplicationLifetime 類型標記為過時並被替換</span><span class="sxs-lookup"><span data-stu-id="eadab-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="eadab-102">引入了新的類型來替換現有`IHostingEnvironment`類型和`IApplicationLifetime`類型。</span><span class="sxs-lookup"><span data-stu-id="eadab-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eadab-103">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="eadab-103">Version introduced</span></span>

<span data-ttu-id="eadab-104">3.0</span><span class="sxs-lookup"><span data-stu-id="eadab-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eadab-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="eadab-105">Old behavior</span></span>

<span data-ttu-id="eadab-106">`IHostingEnvironment`有兩種不同的`IApplicationLifetime`類型和類型從`Microsoft.Extensions.Hosting``Microsoft.AspNetCore.Hosting`和 。</span><span class="sxs-lookup"><span data-stu-id="eadab-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eadab-107">新的行為</span><span class="sxs-lookup"><span data-stu-id="eadab-107">New behavior</span></span>

<span data-ttu-id="eadab-108">舊類型已標記為過時，並替換為新類型。</span><span class="sxs-lookup"><span data-stu-id="eadab-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eadab-109">更改原因</span><span class="sxs-lookup"><span data-stu-id="eadab-109">Reason for change</span></span>

<span data-ttu-id="eadab-110">在`Microsoft.Extensions.Hosting`ASP.NET Core 2.1 中引入時`IHostingEnvironment`，`IApplicationLifetime`某些類型（`Microsoft.AspNetCore.Hosting`如 和）是從 中複製的。</span><span class="sxs-lookup"><span data-stu-id="eadab-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="eadab-111">某些ASP.NET Core 3.0 更改會導致應用同時`Microsoft.Extensions.Hosting`包含`Microsoft.AspNetCore.Hosting`和 命名空間。</span><span class="sxs-lookup"><span data-stu-id="eadab-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="eadab-112">引用兩個命名空間時，對這些重複類型的任何使用都會導致"模糊引用"編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="eadab-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eadab-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="eadab-113">Recommended action</span></span>

<span data-ttu-id="eadab-114">將舊類型的任何用法替換為新引入的類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="eadab-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="eadab-115">**過時類型（警告）：**</span><span class="sxs-lookup"><span data-stu-id="eadab-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="eadab-116">**新類型：**</span><span class="sxs-lookup"><span data-stu-id="eadab-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="eadab-117">新的`IHostEnvironment``IsDevelopment`和`IsProduction`擴充方法在`Microsoft.Extensions.Hosting`命名空間中。</span><span class="sxs-lookup"><span data-stu-id="eadab-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="eadab-118">可能需要將命名空間添加到專案中。</span><span class="sxs-lookup"><span data-stu-id="eadab-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="eadab-119">類別</span><span class="sxs-lookup"><span data-stu-id="eadab-119">Category</span></span>

<span data-ttu-id="eadab-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eadab-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eadab-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="eadab-121">Affected APIs</span></span>

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
