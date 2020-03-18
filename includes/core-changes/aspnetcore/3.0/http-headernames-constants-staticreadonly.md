---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901659"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="78c4a-101">HTTP：標題名稱常量更改為靜態唯讀</span><span class="sxs-lookup"><span data-stu-id="78c4a-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="78c4a-102">從 ASP.NET 酷 3.0 預覽 5<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>中`const`開始`static readonly`，中的欄位從 更改為 。</span><span class="sxs-lookup"><span data-stu-id="78c4a-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="78c4a-103">有關討論，請參閱[點網/阿斯平核心@9514](https://github.com/dotnet/aspnetcore/issues/9514)。</span><span class="sxs-lookup"><span data-stu-id="78c4a-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="78c4a-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="78c4a-104">Version introduced</span></span>

<span data-ttu-id="78c4a-105">3.0</span><span class="sxs-lookup"><span data-stu-id="78c4a-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="78c4a-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="78c4a-106">Old behavior</span></span>

<span data-ttu-id="78c4a-107">這些欄位過去是`const`。</span><span class="sxs-lookup"><span data-stu-id="78c4a-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="78c4a-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="78c4a-108">New behavior</span></span>

<span data-ttu-id="78c4a-109">這些欄位現在是`static readonly`。</span><span class="sxs-lookup"><span data-stu-id="78c4a-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="78c4a-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="78c4a-110">Reason for change</span></span>

<span data-ttu-id="78c4a-111">更改：</span><span class="sxs-lookup"><span data-stu-id="78c4a-111">The change:</span></span>

* <span data-ttu-id="78c4a-112">防止將值嵌入到裝配體邊界之間，從而允許根據需要進行值校正。</span><span class="sxs-lookup"><span data-stu-id="78c4a-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="78c4a-113">實現更快的引用相等性檢查。</span><span class="sxs-lookup"><span data-stu-id="78c4a-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="78c4a-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="78c4a-114">Recommended action</span></span>

<span data-ttu-id="78c4a-115">針對 3.0 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="78c4a-115">Recompile against 3.0.</span></span> <span data-ttu-id="78c4a-116">以下列方式使用這些欄位的原始程式碼不能再這樣做：</span><span class="sxs-lookup"><span data-stu-id="78c4a-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="78c4a-117">作為屬性參數</span><span class="sxs-lookup"><span data-stu-id="78c4a-117">As an attribute argument</span></span>
* <span data-ttu-id="78c4a-118">作為語句`case`中的一`switch`個</span><span class="sxs-lookup"><span data-stu-id="78c4a-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="78c4a-119">定義另一個時`const`</span><span class="sxs-lookup"><span data-stu-id="78c4a-119">When defining another `const`</span></span>

<span data-ttu-id="78c4a-120">要解決突發性更改，請切換到使用自訂的標頭名稱常量或字串文本。</span><span class="sxs-lookup"><span data-stu-id="78c4a-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="78c4a-121">類別</span><span class="sxs-lookup"><span data-stu-id="78c4a-121">Category</span></span>

<span data-ttu-id="78c4a-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="78c4a-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="78c4a-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="78c4a-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
