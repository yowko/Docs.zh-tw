---
title: x:Members 指示詞
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: c751a4f1cdea8dce7ef5165f5225ab3a825c7344
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071462"
---
# <a name="xmembers-directive"></a><span data-ttu-id="fcdf8-102">x:Members 指示詞</span><span class="sxs-lookup"><span data-stu-id="fcdf8-102">x:Members Directive</span></span>
<span data-ttu-id="fcdf8-103">保存在標記中定義的一組成員,該成員適用於父元素的 x:類。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="fcdf8-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="fcdf8-104">XAML Attribute Usage</span></span>

```xaml
<object x:Class="className">
<x:Members>
  oneOrMoreMembers
</x:Members
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="fcdf8-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="fcdf8-105">XAML Values</span></span>

|||
|-|-|
|`className`|<span data-ttu-id="fcdf8-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="fcdf8-107">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-107">See Remarks.</span></span>|
|`oneOrMoreMembers`|<span data-ttu-id="fcdf8-108">表示成員定義的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="fcdf8-109">通常,這些是`x:Property`物件元素。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="fcdf8-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-110">See Remarks.</span></span>|

## <a name="remarks"></a><span data-ttu-id="fcdf8-111">備註</span><span class="sxs-lookup"><span data-stu-id="fcdf8-111">Remarks</span></span>

<span data-ttu-id="fcdf8-112">在 .NET XAML 服務實現中`x:Members`,沒有支援類或基礎成員實現。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-112">In .NET XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="fcdf8-113">`x:Members`是可作為任何類型的成員存在的特殊 XAML 成員。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="fcdf8-114">在 XAML`x:Members`節點流 中,從 XAML 語言 XAML 命名空間中表示為名為`Members`的成員。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="fcdf8-115">該成員`Members``Member`包含 物件的唯讀泛型清單。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="fcdf8-116">在典型的標記中,單個成員被指定為`x:Property`屬性元素。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="fcdf8-117">`x:Property`是專門針對類型屬性的更精確的類型,可分配給`x:Member`。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="fcdf8-118">有關詳細資訊,請參閱[x:屬性指令](xproperty-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-118">For more information, see [x:Property Directive](xproperty-directive.md).</span></span>

<span data-ttu-id="fcdf8-119">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="fcdf8-120">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="fcdf8-121">但是,在 .NET XAML 服務級別不支援關聯類型和成員或生成動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at .NET XAML Services level.</span></span> <span data-ttu-id="fcdf8-122">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="fcdf8-123">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>

## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="fcdf8-124">X:Windows 工作流基礎的成員</span><span class="sxs-lookup"><span data-stu-id="fcdf8-124">x:Members for Windows Workflow Foundation</span></span>

<span data-ttu-id="fcdf8-125">對於 Windows`x:Members`工作流基礎,包含完全以 XAML 或 XAML — 定義具有代碼後面的活動設計器的動態成員組成的自定義活動的成員。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="fcdf8-126">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="fcdf8-127">這不是 .NET XAML 服務級別的要求,但當支援自定義活動和 Windows 工作流基礎 XAML 的 MSBUILD 生成操作載入 XAML 生產時,這將成為一項要求。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-127">This is not a requirement at .NET XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="fcdf8-128">`x:Members`必須是宣告的物件元素標記中的第一個子元素`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="fcdf8-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
