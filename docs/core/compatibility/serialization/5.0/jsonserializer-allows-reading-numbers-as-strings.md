---
title: 重大變更： ASP.NET Core apps 允許將引號數位還原序列化
description: 瞭解 .NET 5.0 中的重大變更，其中 ASP.NET Core apps 會成功將表示為 JSON 字串的數位還原序列化，而不是擲回例外狀況。
ms.date: 10/21/2020
ms.openlocfilehash: fc8a4c6638be391c22c7cfb2fc7c216c88377f29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760605"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="c9287-103">ASP.NET Core apps 允許將引號數位還原序列化</span><span class="sxs-lookup"><span data-stu-id="c9287-103">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="c9287-104">從 .NET 5.0 開始，ASP.NET Core apps 會使用所指定的預設還原序列化選項 <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-104">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c9287-105"><xref:System.Text.Json.JsonSerializerDefaults.Web>選項組包括將設定 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> 為 <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-105">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c9287-106">這項變更表示 ASP.NET Core apps 將會成功將以 JSON 字串表示的數位還原序列化，而不是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c9287-106">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings instead of throwing an exception.</span></span>

## <a name="change-description"></a><span data-ttu-id="c9287-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="c9287-107">Change description</span></span>

<span data-ttu-id="c9287-108">在 .NET Core 3.0-3.1 中， <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> 如果在 JSON 承載中遇到引號數位，則會在還原序列化期間擲回。</span><span class="sxs-lookup"><span data-stu-id="c9287-108">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="c9287-109">以引號括住的數位會用來對應物件圖形中的數位屬性。</span><span class="sxs-lookup"><span data-stu-id="c9287-109">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="c9287-110">在 .NET Core 3.0-3.1 中，只會從標記讀取數位 <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-110">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="c9287-111">從 .NET 5.0 開始，JSON 承載中括住的數位預設會被視為適用于 ASP.NET Core apps。</span><span class="sxs-lookup"><span data-stu-id="c9287-111">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="c9287-112">在還原序列化引號中的數位時，不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c9287-112">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="c9287-113">預設的獨立或沒有任何行為變更 <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonSerializerOptions> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-113">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="c9287-114">這在技術上並不是一項重大變更，因為它會讓案例更寬鬆，而不是更嚴格的 (也就是說，它會成功從 JSON 字串強制執行一個數位，而不是擲回例外狀況) 。</span><span class="sxs-lookup"><span data-stu-id="c9287-114">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="c9287-115">不過，由於這是影響許多 ASP.NET Core 應用程式的重大行為變更，因此會記載于此處。</span><span class="sxs-lookup"><span data-stu-id="c9287-115">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="c9287-116"><xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType>和 <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> 擴充方法也會使用 <xref:System.Text.Json.JsonSerializerDefaults.Web> 一組序列化選項。</span><span class="sxs-lookup"><span data-stu-id="c9287-116">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c9287-117">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c9287-117">Version introduced</span></span>

<span data-ttu-id="c9287-118">5.0</span><span class="sxs-lookup"><span data-stu-id="c9287-118">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c9287-119">變更的原因</span><span class="sxs-lookup"><span data-stu-id="c9287-119">Reason for change</span></span>

<span data-ttu-id="c9287-120">多個使用者已在中要求更寬鬆的數位處理選項 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-120">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="c9287-121">這種意見反應表示許多 JSON 生產者 (例如，跨 web) 的服務會發出加引號的數位。</span><span class="sxs-lookup"><span data-stu-id="c9287-121">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="c9287-122">藉由允許將引號的數位讀取 (還原序列化的) ，.NET 應用程式在 web 內容中預設可以成功剖析這些承載。</span><span class="sxs-lookup"><span data-stu-id="c9287-122">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="c9287-123">設定會透過公開， <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> 讓您可以在不同的應用層（例如用戶端、伺服器和共用）之間指定相同的選項。</span><span class="sxs-lookup"><span data-stu-id="c9287-123">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c9287-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c9287-124">Recommended action</span></span>

<span data-ttu-id="c9287-125">如果這項變更是干擾性的，例如，如果您相依于驗證的嚴格數位處理，您可以重新啟用先前的行為。</span><span class="sxs-lookup"><span data-stu-id="c9287-125">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="c9287-126">將 <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> 選項設定為 <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c9287-126">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c9287-127">針對 ASP.NET Core MVC 和 web API 應用程式，您可以 `Startup` 使用下列程式碼來設定中的選項：</span><span class="sxs-lookup"><span data-stu-id="c9287-127">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a><span data-ttu-id="c9287-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c9287-128">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
