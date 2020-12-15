---
title: 重大變更： Blazor： Blazor apps 中的路由邏輯變更
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： Blazor apps 中的路由邏輯變更
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513518"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a><span data-ttu-id="be21d-103">Blazor： Blazor apps 中的路由優先順序邏輯已變更</span><span class="sxs-lookup"><span data-stu-id="be21d-103">Blazor: Route precedence logic changed in Blazor apps</span></span>

<span data-ttu-id="be21d-104">Blazor 路由執行中的錯誤會影響路由的優先順序決定方式。</span><span class="sxs-lookup"><span data-stu-id="be21d-104">A bug in the Blazor routing implementation affected how the precedence of routes was determined.</span></span> <span data-ttu-id="be21d-105">此錯誤會在您的 Blazor 應用程式內使用選擇性參數來影響全部攔截路由或路由。</span><span class="sxs-lookup"><span data-stu-id="be21d-105">This bug affects catch-all routes or routes with optional parameters within your Blazor app.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="be21d-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="be21d-106">Version introduced</span></span>

<span data-ttu-id="be21d-107">5.0.1</span><span class="sxs-lookup"><span data-stu-id="be21d-107">5.0.1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="be21d-108">舊的行為</span><span class="sxs-lookup"><span data-stu-id="be21d-108">Old behavior</span></span>

<span data-ttu-id="be21d-109">使用錯誤的行為時，會考慮優先順序較低的路由，並透過優先順序較高的路由進行比對。</span><span class="sxs-lookup"><span data-stu-id="be21d-109">With the erroneous behavior, routes with lower precedence are considered and matched over routes with higher precedence.</span></span> <span data-ttu-id="be21d-110">例如， `{*slug}` 路由會先符合 `/customer/{id}` 。</span><span class="sxs-lookup"><span data-stu-id="be21d-110">For example, the `{*slug}` route is matched before `/customer/{id}`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="be21d-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="be21d-111">New behavior</span></span>

<span data-ttu-id="be21d-112">目前的行為更緊密符合 ASP.NET Core apps 中定義的路由行為。</span><span class="sxs-lookup"><span data-stu-id="be21d-112">The current behavior more closely matches the routing behavior defined in ASP.NET Core apps.</span></span> <span data-ttu-id="be21d-113">架構會先判斷每個區段的路由優先順序。</span><span class="sxs-lookup"><span data-stu-id="be21d-113">The framework determines the route precedence for each segment first.</span></span> <span data-ttu-id="be21d-114">路由的長度只會用來做為中斷系結的第二個準則。</span><span class="sxs-lookup"><span data-stu-id="be21d-114">The route's length is used only as a second criteria to break ties.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="be21d-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="be21d-115">Reason for change</span></span>

<span data-ttu-id="be21d-116">原始行為在執行時視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="be21d-116">The original behavior is considered a bug in the implementation.</span></span> <span data-ttu-id="be21d-117">作為目標，Blazor apps 中的路由系統在 ASP.NET Core 的其餘部分應該與路由系統的行為方式相同。</span><span class="sxs-lookup"><span data-stu-id="be21d-117">As a goal, the routing system in Blazor apps should behave the same way as the routing system in the rest of ASP.NET Core.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="be21d-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="be21d-118">Recommended action</span></span>

<span data-ttu-id="be21d-119">如果從舊版 Blazor 升級為5.x，請使用 `PreferExactMatches` 元件上的屬性 `Router` 。</span><span class="sxs-lookup"><span data-stu-id="be21d-119">If upgrading from previous versions of Blazor to 5.x, use the `PreferExactMatches` attribute on the `Router` component.</span></span> <span data-ttu-id="be21d-120">這個屬性可用來選擇使用正確的行為。</span><span class="sxs-lookup"><span data-stu-id="be21d-120">This attribute can be used to opt into the correct behavior.</span></span> <span data-ttu-id="be21d-121">例如︰</span><span class="sxs-lookup"><span data-stu-id="be21d-121">For example:</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

<span data-ttu-id="be21d-122">當 `PreferExactMatches` 設定為時 `true` ，路由比對會優先于萬用字元的完全相符專案。</span><span class="sxs-lookup"><span data-stu-id="be21d-122">When `PreferExactMatches` is set to `true`, route matching prefers exact matches over wildcards.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="be21d-123">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="be21d-123">Affected APIs</span></span>

<span data-ttu-id="be21d-124">無</span><span class="sxs-lookup"><span data-stu-id="be21d-124">None</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
