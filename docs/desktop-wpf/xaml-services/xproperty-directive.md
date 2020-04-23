---
title: x:Property 指示詞
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 2804ec935d0626cba9ef050f70a3266cf23bcce0
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071406"
---
# <a name="xproperty-directive"></a><span data-ttu-id="e092c-102">x:Property 指示詞</span><span class="sxs-lookup"><span data-stu-id="e092c-102">x:Property Directive</span></span>

<span data-ttu-id="e092c-103">在標記中宣告 XAML 屬性。</span><span class="sxs-lookup"><span data-stu-id="e092c-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="e092c-104">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="e092c-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="e092c-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="e092c-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="e092c-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="e092c-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="e092c-107">正在定義之屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="e092c-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="e092c-108">指定這個屬性類型的類型名稱 (或其他特定架構的字串形式)。</span><span class="sxs-lookup"><span data-stu-id="e092c-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e092c-109">備註</span><span class="sxs-lookup"><span data-stu-id="e092c-109">Remarks</span></span>

<span data-ttu-id="e092c-110">在 .NET XAML 服務實現中,</span><span class="sxs-lookup"><span data-stu-id="e092c-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="e092c-111">`x:Property` 沒有直接的類型支援，但受到 <xref:System.Windows.Markup.PropertyDefinition> 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="e092c-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="e092c-112">在 XAML 節點資料流中，`x:Property` 項目會以 XAML 語言 XAML 命名空間中名為 `Property` 的成員表示。</span><span class="sxs-lookup"><span data-stu-id="e092c-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="e092c-113">成員 `Property` 包含依標記宣告的屬性。</span><span class="sxs-lookup"><span data-stu-id="e092c-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="e092c-114">的表示義`Name``Type`不在 .NET XAML 服務級別分配。</span><span class="sxs-lookup"><span data-stu-id="e092c-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="e092c-115">它們會在初始 XAML 節點資料流中儲存為字串值，以便稍後依據特定架構可能加諸的規則解譯。</span><span class="sxs-lookup"><span data-stu-id="e092c-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="e092c-116">這個意義可能與 XAML 名稱和 XAML 類型的意義一致，或可能只是在支援類型系統中有效，視實作而定。</span><span class="sxs-lookup"><span data-stu-id="e092c-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="e092c-117">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="e092c-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="e092c-118">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="e092c-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="e092c-119">但是,在 .NET XAML 服務級別不支援關聯類型和成員或生成動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="e092c-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="e092c-120">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="e092c-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="e092c-121">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="e092c-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="e092c-122">Windows Workflow Foundation 的 x:Property</span><span class="sxs-lookup"><span data-stu-id="e092c-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="e092c-123">針對 Windows Workflow Foundation，`x:Property` 會定義完全以 XAML 撰寫之自訂活動的成員，或程式碼後置活動設計工具的 XAML 定義動態成員。</span><span class="sxs-lookup"><span data-stu-id="e092c-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="e092c-124">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="e092c-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="e092c-125">這不是 .NET XAML 服務級別的要求,但當支援自定義活動和 Windows 工作流基礎 XAML 的 MSBUILD 生成操作載入 XAML 生產時,這將成為一項要求。</span><span class="sxs-lookup"><span data-stu-id="e092c-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="e092c-126">Windows 工作流基礎不使用純 XAML 類型`x:Property``Type`名稱作為其 屬性的預期值,而是使用此處未記錄的約定。</span><span class="sxs-lookup"><span data-stu-id="e092c-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="e092c-127">有關詳細資訊,請參閱[動態活動建立](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e092c-127">For more information, see [DynamicActivity Creation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
