---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032360"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="870d1-101">HTTP： HeaderNames 常數已變更為靜態 readonly</span><span class="sxs-lookup"><span data-stu-id="870d1-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="870d1-102">從 ASP.NET Core 3.0 Preview 5 開始，中的欄位 <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 已從變更 `const` 為 `static readonly` 。</span><span class="sxs-lookup"><span data-stu-id="870d1-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="870d1-103">如需討論，請參閱 [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514)。</span><span class="sxs-lookup"><span data-stu-id="870d1-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="870d1-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="870d1-104">Version introduced</span></span>

<span data-ttu-id="870d1-105">3.0</span><span class="sxs-lookup"><span data-stu-id="870d1-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="870d1-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="870d1-106">Old behavior</span></span>

<span data-ttu-id="870d1-107">這些欄位是用來做為 `const` 。</span><span class="sxs-lookup"><span data-stu-id="870d1-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="870d1-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="870d1-108">New behavior</span></span>

<span data-ttu-id="870d1-109">這些欄位現在是 `static readonly` 。</span><span class="sxs-lookup"><span data-stu-id="870d1-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="870d1-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="870d1-110">Reason for change</span></span>

<span data-ttu-id="870d1-111">變更：</span><span class="sxs-lookup"><span data-stu-id="870d1-111">The change:</span></span>

* <span data-ttu-id="870d1-112">防止將值內嵌在元件界限上，以便在需要時進行值修正。</span><span class="sxs-lookup"><span data-stu-id="870d1-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="870d1-113">可加快參考相等檢查的速度。</span><span class="sxs-lookup"><span data-stu-id="870d1-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="870d1-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="870d1-114">Recommended action</span></span>

<span data-ttu-id="870d1-115">針對3.0 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="870d1-115">Recompile against 3.0.</span></span> <span data-ttu-id="870d1-116">以下列方式使用這些欄位的原始程式碼，將無法再執行此動作：</span><span class="sxs-lookup"><span data-stu-id="870d1-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="870d1-117">做為屬性引數</span><span class="sxs-lookup"><span data-stu-id="870d1-117">As an attribute argument</span></span>
* <span data-ttu-id="870d1-118">做為 `case` 語句中 `switch` 的</span><span class="sxs-lookup"><span data-stu-id="870d1-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="870d1-119">定義其他 `const`</span><span class="sxs-lookup"><span data-stu-id="870d1-119">When defining another `const`</span></span>

<span data-ttu-id="870d1-120">若要解決重大變更，請切換到使用自我定義的標頭名稱常數或字串常值。</span><span class="sxs-lookup"><span data-stu-id="870d1-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="870d1-121">類別</span><span class="sxs-lookup"><span data-stu-id="870d1-121">Category</span></span>

<span data-ttu-id="870d1-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="870d1-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="870d1-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="870d1-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
