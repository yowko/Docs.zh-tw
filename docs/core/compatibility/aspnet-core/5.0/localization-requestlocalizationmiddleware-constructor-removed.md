---
title: 重大變更：當地語系化：在要求當地語系化中介軟體中移除已淘汰的函式
description: 瞭解 ASP.NET Core 5.0 的重大變更，其標題為當地語系化：在要求當地語系化中介軟體中移除已淘汰的函式
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760763"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="b6165-103">當地語系化：在要求當地語系化中介軟體中移除過時的函式</span><span class="sxs-lookup"><span data-stu-id="b6165-103">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="b6165-104"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>缺少參數的函式 <xref:Microsoft.Extensions.Logging.ILoggerFactory> [在此認可中](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="b6165-104">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="b6165-105">在 ASP.NET Core 5.0 中，已移除過時的函式。</span><span class="sxs-lookup"><span data-stu-id="b6165-105">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="b6165-106">如需討論，請參閱 [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785)。</span><span class="sxs-lookup"><span data-stu-id="b6165-106">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b6165-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b6165-107">Version introduced</span></span>

<span data-ttu-id="b6165-108">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b6165-108">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b6165-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b6165-109">Old behavior</span></span>

<span data-ttu-id="b6165-110">已淘汰的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 存在。</span><span class="sxs-lookup"><span data-stu-id="b6165-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b6165-111">新的行為</span><span class="sxs-lookup"><span data-stu-id="b6165-111">New behavior</span></span>

<span data-ttu-id="b6165-112">過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 不存在。</span><span class="sxs-lookup"><span data-stu-id="b6165-112">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b6165-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b6165-113">Reason for change</span></span>

<span data-ttu-id="b6165-114">這種變更可確保要求當地語系化中介軟體一律具有記錄器的存取權。</span><span class="sxs-lookup"><span data-stu-id="b6165-114">This change ensures that the request localization middleware always has access to a logger.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b6165-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b6165-115">Recommended action</span></span>

<span data-ttu-id="b6165-116">當您手動建立的實例時 `RequestLocalizationMiddleware` ，會在函式 `ILoggerFactory` 中傳遞實例。</span><span class="sxs-lookup"><span data-stu-id="b6165-116">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="b6165-117">如果 `ILoggerFactory` 該內容中未提供有效的實例，請考慮將中介軟體函式傳遞給 <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> 實例。</span><span class="sxs-lookup"><span data-stu-id="b6165-117">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b6165-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b6165-118">Affected APIs</span></span>

[<span data-ttu-id="b6165-119">RequestLocalizationMiddleware .ctor (RequestDelegate、Microsoft.extensions.options.ioptions \<RequestLocalizationOptions>) </span><span class="sxs-lookup"><span data-stu-id="b6165-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
