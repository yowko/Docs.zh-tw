---
title: x:Property 指示詞
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: d4294b39ff262198f8082863d23eb6f4edbc7054
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549297"
---
# <a name="xproperty-directive"></a><span data-ttu-id="f4d26-102">x:Property 指示詞</span><span class="sxs-lookup"><span data-stu-id="f4d26-102">x:Property Directive</span></span>

<span data-ttu-id="f4d26-103">在標記中宣告 XAML 屬性。</span><span class="sxs-lookup"><span data-stu-id="f4d26-103">Declares a XAML property in markup.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="f4d26-104">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="f4d26-104">XAML Object Element Usage</span></span>

```xaml
<object x:Class="className">
  <x:Members>
    <x:Property Name="propertyName" Type="propertyType"/>
    additionalProperties
  </x:Members>
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="f4d26-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="f4d26-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="f4d26-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d26-106">Name of the backing class or partial class for the XAML production.</span></span>|
|`propertyName`|<span data-ttu-id="f4d26-107">正在定義之屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="f4d26-107">Member name of the property being defined.</span></span>|
|`propertyType`|<span data-ttu-id="f4d26-108">指定這個屬性類型的類型名稱 (或其他特定架構的字串形式)。</span><span class="sxs-lookup"><span data-stu-id="f4d26-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f4d26-109">備註</span><span class="sxs-lookup"><span data-stu-id="f4d26-109">Remarks</span></span>

<span data-ttu-id="f4d26-110">在 .NET XAML 服務的執行中，</span><span class="sxs-lookup"><span data-stu-id="f4d26-110">In .NET XAML Services implementation, .</span></span> <span data-ttu-id="f4d26-111">`x:Property` 沒有直接的類型支援，但受到 <xref:System.Windows.Markup.PropertyDefinition> 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="f4d26-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="f4d26-112">在 XAML 節點資料流中，`x:Property` 項目會以 XAML 語言 XAML 命名空間中名為 `Property` 的成員表示。</span><span class="sxs-lookup"><span data-stu-id="f4d26-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="f4d26-113">成員 `Property` 包含依標記宣告的屬性。</span><span class="sxs-lookup"><span data-stu-id="f4d26-113">The member `Property` hold attributes as declared by markup.</span></span>

<span data-ttu-id="f4d26-114">和的意義 `Name` `Type` 不是在 .Net XAML 服務層級指派。</span><span class="sxs-lookup"><span data-stu-id="f4d26-114">The meaning of `Name` and `Type` are not assigned at .NET XAML Services level.</span></span> <span data-ttu-id="f4d26-115">它們會在初始 XAML 節點資料流中儲存為字串值，以便稍後依據特定架構可能加諸的規則解譯。</span><span class="sxs-lookup"><span data-stu-id="f4d26-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="f4d26-116">這個意義可能與 XAML 名稱和 XAML 類型的意義一致，或可能只是在支援類型系統中有效，視實作而定。</span><span class="sxs-lookup"><span data-stu-id="f4d26-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>

<span data-ttu-id="f4d26-117">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="f4d26-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="f4d26-118">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="f4d26-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="f4d26-119">不過，.NET XAML 服務層級不支援關聯類型和成員或產生動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="f4d26-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="f4d26-120">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="f4d26-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="f4d26-121">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="f4d26-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="f4d26-122">Windows Workflow Foundation 的 x:Property</span><span class="sxs-lookup"><span data-stu-id="f4d26-122">x:Property for Windows Workflow Foundation</span></span>

<span data-ttu-id="f4d26-123">針對 Windows Workflow Foundation，`x:Property` 會定義完全以 XAML 撰寫之自訂活動的成員，或程式碼後置活動設計工具的 XAML 定義動態成員。</span><span class="sxs-lookup"><span data-stu-id="f4d26-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="f4d26-124">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="f4d26-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="f4d26-125">這不是 .NET XAML 服務層級的需求，但在 XAML 生產是由支援自訂活動和一般 Windows Workflow Foundation XAML 的 MSBUILD 組建動作載入時，就會成為需求。</span><span class="sxs-lookup"><span data-stu-id="f4d26-125">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="f4d26-126">Windows Workflow Foundation 不會使用純 XAML 型別名稱做為其預期的 `x:Property` `Type` 屬性值，而是使用此處未記載的慣例。</span><span class="sxs-lookup"><span data-stu-id="f4d26-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="f4d26-127">如需詳細資訊，請參閱 [建立 DynamicActivity](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f4d26-127">For more information, see [DynamicActivity Creation](/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).</span></span>
