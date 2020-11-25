---
title: 重大變更：非公用、無參數的函式未使用於還原序列化
description: 瞭解 .NET 5.0 中的重大變更，其中非公用、無參數的函式不再用於以 JsonSerializer 還原序列化。
ms.date: 10/18/2020
ms.openlocfilehash: 6bdcc92c61008aa4ee27370bbac4dbf4ee3ef7c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760766"
---
# <a name="non-public-parameterless-constructors-not-used-for-deserialization"></a><span data-ttu-id="915c9-103">非公用、無參數的函式不會用於還原序列化</span><span class="sxs-lookup"><span data-stu-id="915c9-103">Non-public, parameterless constructors not used for deserialization</span></span>

<span data-ttu-id="915c9-104">為了在所有支援的目標 framework 標記之間保持一致性 (Tfm) ，非公用的無參數函式預設不會再用於還原序列化 <xref:System.Text.Json.JsonSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="915c9-104">For consistency across all supported target framework monikers (TFMs), non-public, parameterless constructors are no longer used for deserialization with <xref:System.Text.Json.JsonSerializer>, by default.</span></span>

## <a name="change-description"></a><span data-ttu-id="915c9-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="915c9-105">Change description</span></span>

<span data-ttu-id="915c9-106">在支援 .NET Standard 2.0 和更新版本的 [ NuGet 套件上](https://www.nuget.org/packages/System.Text.Json/) 的獨立System.Text.Js（也就是 4.6.0 4.7.2 版本），其行為與 .net Core 3.0 和3.1 上的內建行為不一致。</span><span class="sxs-lookup"><span data-stu-id="915c9-106">The standalone [System.Text.Json NuGet packages](https://www.nuget.org/packages/System.Text.Json/) that support .NET Standard 2.0 and higher, that is, versions 4.6.0-4.7.2, behave inconsistently with the built-in behavior on .NET Core 3.0 and 3.1.</span></span> <span data-ttu-id="915c9-107">在 .NET Core 3.x 上，內部和私用的函式可用於還原序列化。</span><span class="sxs-lookup"><span data-stu-id="915c9-107">On .NET Core 3.x, internal and private constructors can be used for deserialization.</span></span> <span data-ttu-id="915c9-108">在獨立封裝中，不允許非公用的函式，而且 <xref:System.MissingMethodException> 如果沒有定義任何公用的無參數的函式，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="915c9-108">In the standalone packages, non-public constructors are not allowed, and a <xref:System.MissingMethodException> is thrown if no public, parameterless constructor is defined.</span></span>

<span data-ttu-id="915c9-109">從 .NET 5.0 開始，nuget 套件5.0.0 上的 System.Text.Js，NuGet 套件和內建 Api 之間的行為是一致的。</span><span class="sxs-lookup"><span data-stu-id="915c9-109">Starting with .NET 5.0 and System.Text.Json NuGet package 5.0.0, the behavior is consistent between the NuGet package and the built-in APIs.</span></span> <span data-ttu-id="915c9-110">依預設，序列化程式會忽略非公用的函式，包括無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="915c9-110">Non-public constructors, including parameterless constructors, are ignored by the serializer by default.</span></span> <span data-ttu-id="915c9-111">序列化程式會使用下列其中一個用於還原序列化的函式：</span><span class="sxs-lookup"><span data-stu-id="915c9-111">The serializer uses one of the following constructors for deserialization:</span></span>

- <span data-ttu-id="915c9-112">使用批註的公用函式 <xref:System.Text.Json.Serialization.JsonConstructorAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="915c9-112">Public constructor annotated with <xref:System.Text.Json.Serialization.JsonConstructorAttribute>.</span></span>
- <span data-ttu-id="915c9-113">公用無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="915c9-113">Public parameterless constructor.</span></span>
- <span data-ttu-id="915c9-114">公用參數化的函式 (是否為唯一的公用函式) 。</span><span class="sxs-lookup"><span data-stu-id="915c9-114">Public parameterized constructor (if it's the only public constructor present).</span></span>

<span data-ttu-id="915c9-115">如果沒有這些可用的函式， <xref:System.NotSupportedException> 當您嘗試還原序列化類型時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="915c9-115">If none of these constructors are available, a <xref:System.NotSupportedException> is thrown if you attempt to deserialize the type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="915c9-116">引進的版本</span><span class="sxs-lookup"><span data-stu-id="915c9-116">Version introduced</span></span>

<span data-ttu-id="915c9-117">5.0</span><span class="sxs-lookup"><span data-stu-id="915c9-117">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="915c9-118">變更的原因</span><span class="sxs-lookup"><span data-stu-id="915c9-118">Reason for change</span></span>

- <span data-ttu-id="915c9-119">若要在所有目標 framework 標記之間強制執行一致的行為 (可為 <xref:System.Text.Json?displayProperty=fullName> ( .Net Core 3.0 和更新版本的 tfm) ，以及 .NET Standard 2.0) </span><span class="sxs-lookup"><span data-stu-id="915c9-119">To enforce consistent behavior between all target framework monikers (TFMs) that <xref:System.Text.Json?displayProperty=fullName> builds for (.NET Core 3.0 and later versions and .NET Standard 2.0)</span></span>
- <span data-ttu-id="915c9-120">因為 <xref:System.Text.Json.JsonSerializer> 不應該呼叫類型的非公用介面區，無論是函式、屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="915c9-120">Because <xref:System.Text.Json.JsonSerializer> shouldn't call the non-public surface area of a type, whether that's a constructor, a property, or a field.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="915c9-121">建議的動作</span><span class="sxs-lookup"><span data-stu-id="915c9-121">Recommended action</span></span>

- <span data-ttu-id="915c9-122">如果您擁有類型且可行，請將無參數的函式設為公用。</span><span class="sxs-lookup"><span data-stu-id="915c9-122">If you own the type and it's feasible, make the parameterless constructor public.</span></span>
- <span data-ttu-id="915c9-123">否則，請 `JsonConverter<T>` 針對類型執行，並控制還原序列化行為。</span><span class="sxs-lookup"><span data-stu-id="915c9-123">Otherwise, implement a `JsonConverter<T>` for the type and control the deserialization behavior.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="915c9-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="915c9-124">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
