---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901659"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="5703b-101">HTTP： HeaderNames 常數已變更為靜態 readonly</span><span class="sxs-lookup"><span data-stu-id="5703b-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="5703b-102">從 ASP.NET Core 3.0 Preview 5 開始，<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> 中的欄位從 `const` 變更為 `static readonly`。</span><span class="sxs-lookup"><span data-stu-id="5703b-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="5703b-103">如需討論，請參閱[dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514)。</span><span class="sxs-lookup"><span data-stu-id="5703b-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5703b-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="5703b-104">Version introduced</span></span>

<span data-ttu-id="5703b-105">3.0</span><span class="sxs-lookup"><span data-stu-id="5703b-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5703b-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="5703b-106">Old behavior</span></span>

<span data-ttu-id="5703b-107">這些欄位是用來 `const`。</span><span class="sxs-lookup"><span data-stu-id="5703b-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5703b-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="5703b-108">New behavior</span></span>

<span data-ttu-id="5703b-109">這些欄位現在 `static readonly`。</span><span class="sxs-lookup"><span data-stu-id="5703b-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5703b-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="5703b-110">Reason for change</span></span>

<span data-ttu-id="5703b-111">變更：</span><span class="sxs-lookup"><span data-stu-id="5703b-111">The change:</span></span>

* <span data-ttu-id="5703b-112">防止跨元件界限內嵌值，以允許視需要進行值更正。</span><span class="sxs-lookup"><span data-stu-id="5703b-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="5703b-113">啟用更快速的參考相等檢查。</span><span class="sxs-lookup"><span data-stu-id="5703b-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5703b-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="5703b-114">Recommended action</span></span>

<span data-ttu-id="5703b-115">針對3.0 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="5703b-115">Recompile against 3.0.</span></span> <span data-ttu-id="5703b-116">以下列方式使用這些欄位的原始程式碼不會再這麼做：</span><span class="sxs-lookup"><span data-stu-id="5703b-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="5703b-117">做為屬性引數</span><span class="sxs-lookup"><span data-stu-id="5703b-117">As an attribute argument</span></span>
* <span data-ttu-id="5703b-118">做為 `switch` 語句中的 `case`</span><span class="sxs-lookup"><span data-stu-id="5703b-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="5703b-119">當定義另一個 `const`</span><span class="sxs-lookup"><span data-stu-id="5703b-119">When defining another `const`</span></span>

<span data-ttu-id="5703b-120">若要解決中斷性變更，請切換至使用自我定義的標頭名稱常數或字串常值。</span><span class="sxs-lookup"><span data-stu-id="5703b-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="5703b-121">分類</span><span class="sxs-lookup"><span data-stu-id="5703b-121">Category</span></span>

<span data-ttu-id="5703b-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5703b-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5703b-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="5703b-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
