---
ms.openlocfilehash: b1d4b69b7a8ed68cd688dfd0249d5107b80e67c4
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281331"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="90e7a-101">當地語系化：已在要求當地語系化中介軟體中移除過時的函式</span><span class="sxs-lookup"><span data-stu-id="90e7a-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="90e7a-102"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> <xref:Microsoft.Extensions.Logging.ILoggerFactory> [在此認可中](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)，缺少參數的函式已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="90e7a-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="90e7a-103">在 ASP.NET Core 5.0 中，已移除過時的函式。</span><span class="sxs-lookup"><span data-stu-id="90e7a-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="90e7a-104">如需討論，請參閱[dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785)。</span><span class="sxs-lookup"><span data-stu-id="90e7a-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="90e7a-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="90e7a-105">Version introduced</span></span>

<span data-ttu-id="90e7a-106">5.0</span><span class="sxs-lookup"><span data-stu-id="90e7a-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="90e7a-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="90e7a-107">Old behavior</span></span>

<span data-ttu-id="90e7a-108">已過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 存在。</span><span class="sxs-lookup"><span data-stu-id="90e7a-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="90e7a-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="90e7a-109">New behavior</span></span>

<span data-ttu-id="90e7a-110">過時的函式 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` 不存在。</span><span class="sxs-lookup"><span data-stu-id="90e7a-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="90e7a-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="90e7a-111">Reason for change</span></span>

<span data-ttu-id="90e7a-112">這種變更可確保要求當地語系化中介軟體一律具有記錄器的存取權。</span><span class="sxs-lookup"><span data-stu-id="90e7a-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="90e7a-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="90e7a-113">Recommended action</span></span>

<span data-ttu-id="90e7a-114">當您手動建立的實例時 `RequestLocalizationMiddleware` ，請 `ILoggerFactory` 在此函式中傳遞實例。</span><span class="sxs-lookup"><span data-stu-id="90e7a-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="90e7a-115">如果 `ILoggerFactory` 在該內容中無法使用有效的實例，請考慮將中介軟體的函式傳遞給 <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> 實例。</span><span class="sxs-lookup"><span data-stu-id="90e7a-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="90e7a-116">類別</span><span class="sxs-lookup"><span data-stu-id="90e7a-116">Category</span></span>

<span data-ttu-id="90e7a-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="90e7a-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="90e7a-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="90e7a-118">Affected APIs</span></span>

[<span data-ttu-id="90e7a-119">RequestLocalizationMiddleware (RequestDelegate，Microsoft.extensions.options.ioptions \<RequestLocalizationOptions>) </span><span class="sxs-lookup"><span data-stu-id="90e7a-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
