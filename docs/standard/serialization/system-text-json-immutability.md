---
title: 如何搭配使用不可變類型和非公用存取子 System.Text.Json
description: 瞭解如何在 .NET 中序列化和還原序列化時，使用不可變類型和非公用存取子。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439902"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="d01dc-103">如何搭配使用不可變類型和非公用存取子 System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="d01dc-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="d01dc-104">在本文中，您將學習如何使用不可變的類型（例如記錄）搭配 `System.Text.Json` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d01dc-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="d01dc-105">不可變的類型和記錄</span><span class="sxs-lookup"><span data-stu-id="d01dc-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="d01dc-106">`System.Text.Json` 可以使用參數化的函式，讓您可以還原序列化不可變的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="d01dc-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="d01dc-107">針對類別，如果唯一的函式是參數化的，則會使用該函數。</span><span class="sxs-lookup"><span data-stu-id="d01dc-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="d01dc-108">若為結構或具有多個函式的類別，請套用 [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) 屬性，以指定要使用的類別。</span><span class="sxs-lookup"><span data-stu-id="d01dc-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="d01dc-109">未使用屬性時，一律會使用公用無參數的函式（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="d01dc-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="d01dc-110">屬性只能搭配公用的函式使用。</span><span class="sxs-lookup"><span data-stu-id="d01dc-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="d01dc-111">下列範例會使用 `[JsonConstructor]` 屬性：</span><span class="sxs-lookup"><span data-stu-id="d01dc-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="d01dc-112">也支援 c # 9 中的記錄，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d01dc-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="d01dc-113">針對不可變的類型，因為其所有屬性 setter 都非公用，請參閱下一節有關 [非公用屬性存取](#non-public-property-accessors)子的資訊。</span><span class="sxs-lookup"><span data-stu-id="d01dc-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="d01dc-114">`JsonConstructorAttribute` 和 c # 9 記錄支援在 .NET Core 3.1 中無法使用。</span><span class="sxs-lookup"><span data-stu-id="d01dc-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="d01dc-115">非公用屬性存取子</span><span class="sxs-lookup"><span data-stu-id="d01dc-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="d01dc-116">若要允許使用非公用屬性存取子，請使用 [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d01dc-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="d01dc-117">.NET Core 3.1 不支援非公用屬性存取子。</span><span class="sxs-lookup"><span data-stu-id="d01dc-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="d01dc-118">如需詳細資訊，請參閱「 [從 Newtonsoft.Json 文章遷移](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters)」。</span><span class="sxs-lookup"><span data-stu-id="d01dc-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="d01dc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d01dc-119">See also</span></span>

* [<span data-ttu-id="d01dc-120">System.Text.Json 概述</span><span class="sxs-lookup"><span data-stu-id="d01dc-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="d01dc-121">具現化 JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="d01dc-121">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="d01dc-122">啟用不區分大小寫的比對</span><span class="sxs-lookup"><span data-stu-id="d01dc-122">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="d01dc-123">自訂屬性名稱和值</span><span class="sxs-lookup"><span data-stu-id="d01dc-123">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="d01dc-124">略過屬性</span><span class="sxs-lookup"><span data-stu-id="d01dc-124">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="d01dc-125">允許不正確 JSON</span><span class="sxs-lookup"><span data-stu-id="d01dc-125">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="d01dc-126">處理溢位 JSON</span><span class="sxs-lookup"><span data-stu-id="d01dc-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="d01dc-127">保留迴圈參考</span><span class="sxs-lookup"><span data-stu-id="d01dc-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="d01dc-128">多型序列化</span><span class="sxs-lookup"><span data-stu-id="d01dc-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="d01dc-129">[System.Text.Json API 參考](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d01dc-129">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
