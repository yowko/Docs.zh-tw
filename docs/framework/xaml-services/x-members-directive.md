---
title: x:Members 指示詞
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053760"
---
# <a name="xmembers-directive"></a><span data-ttu-id="f701f-102">x:Members 指示詞</span><span class="sxs-lookup"><span data-stu-id="f701f-102">x:Members Directive</span></span>
<span data-ttu-id="f701f-103">保留一組定義于標記中的成員，其適用于父元素的 X：Class。</span><span class="sxs-lookup"><span data-stu-id="f701f-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="f701f-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="f701f-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="f701f-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="f701f-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="f701f-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="f701f-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="f701f-107">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="f701f-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="f701f-108">一或多個代表成員定義的物件元素。</span><span class="sxs-lookup"><span data-stu-id="f701f-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="f701f-109">一般而言，這些是`x:Property`物件元素。</span><span class="sxs-lookup"><span data-stu-id="f701f-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="f701f-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="f701f-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f701f-111">備註</span><span class="sxs-lookup"><span data-stu-id="f701f-111">Remarks</span></span>  
 <span data-ttu-id="f701f-112">在 .NET Framework XAML 服務執行中，沒有的`x:Members`支援類別或基礎成員執行。</span><span class="sxs-lookup"><span data-stu-id="f701f-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="f701f-113">`x:Members`是特殊的 XAML 成員，可以在任何類型上當做成員存在。</span><span class="sxs-lookup"><span data-stu-id="f701f-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="f701f-114">在 xaml 節點資料流程中， `x:Members`會以 xaml 語言 xaml 命名`Members`空間中名為的成員表示。</span><span class="sxs-lookup"><span data-stu-id="f701f-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="f701f-115">成員`Members`包含`Member`物件的唯讀泛型清單。</span><span class="sxs-lookup"><span data-stu-id="f701f-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="f701f-116">在一般的標記中，會將個別`x:Property`成員指定為屬性元素。</span><span class="sxs-lookup"><span data-stu-id="f701f-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="f701f-117">`x:Property`是更精確的類型，專門用於類型的屬性，而且可`x:Member`指派給。</span><span class="sxs-lookup"><span data-stu-id="f701f-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="f701f-118">如需詳細資訊，請參閱[x:Property](x-property-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="f701f-118">For more information, see [x:Property Directive](x-property-directive.md).</span></span>  
  
 <span data-ttu-id="f701f-119">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="f701f-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="f701f-120">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="f701f-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="f701f-121">不過，.NET Framework XAML 服務層級不支援關聯類型與成員或產生動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="f701f-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="f701f-122">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="f701f-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="f701f-123">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="f701f-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="f701f-124">Windows Workflow Foundation 的 x:Members</span><span class="sxs-lookup"><span data-stu-id="f701f-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="f701f-125">針對 Windows Workflow Foundation， `x:Members`包含完全以 xaml 撰寫之自訂活動的成員，或是包含程式碼後置之活動設計工具的 xaml 定義動態成員。</span><span class="sxs-lookup"><span data-stu-id="f701f-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="f701f-126">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="f701f-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="f701f-127">這不是 .NET Framework XAML 服務層級的需求，但是當 XAML 生產是由支援自訂活動和 Windows Workflow Foundation XAML 的 MSBUILD 建置動作載入時，通常會變成需求。</span><span class="sxs-lookup"><span data-stu-id="f701f-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="f701f-128">`x:Members`必須是宣告之物件元素`x:Class`標記中的第一個子專案。</span><span class="sxs-lookup"><span data-stu-id="f701f-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
