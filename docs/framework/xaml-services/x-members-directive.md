---
title: "x:Members 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e76f539e713f3d21751de18c86cc2dcebf99f570
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xmembers-directive"></a><span data-ttu-id="bbcde-102">x:Members 指示詞</span><span class="sxs-lookup"><span data-stu-id="bbcde-102">x:Members Directive</span></span>
<span data-ttu-id="bbcde-103">保存成員定義在標記中，套用至父項目 x： 類別的集合。</span><span class="sxs-lookup"><span data-stu-id="bbcde-103">Holds a set of members that are defined in markup, which apply to the x:Class of the parent element.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="bbcde-104">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="bbcde-104">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="bbcde-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="bbcde-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="bbcde-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="bbcde-106">Name of the backing class or partial class for the XAML production.</span></span> <span data-ttu-id="bbcde-107">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="bbcde-107">See Remarks.</span></span>|  
|`oneOrMoreMembers`|<span data-ttu-id="bbcde-108">代表成員定義的一個或多個物件元素。</span><span class="sxs-lookup"><span data-stu-id="bbcde-108">One or more object elements that represent member definitions.</span></span> <span data-ttu-id="bbcde-109">一般來說，這些是`x:Property`物件項目。</span><span class="sxs-lookup"><span data-stu-id="bbcde-109">Typically, these are `x:Property` object elements.</span></span> <span data-ttu-id="bbcde-110">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="bbcde-110">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbcde-111">備註</span><span class="sxs-lookup"><span data-stu-id="bbcde-111">Remarks</span></span>  
 <span data-ttu-id="bbcde-112">在.NET Framework XAML 服務實作中，不會支援類別，也為基礎的成員實作`x:Members`。</span><span class="sxs-lookup"><span data-stu-id="bbcde-112">In the .NET Framework XAML Services implementation, there is no backing class or underlying member implementation for `x:Members`.</span></span> <span data-ttu-id="bbcde-113">`x:Members`是特殊的 XAML 成員，可以存在於任何型別上的成員。</span><span class="sxs-lookup"><span data-stu-id="bbcde-113">`x:Members` is a special XAML member that can exist as a member on any type.</span></span> <span data-ttu-id="bbcde-114">在 XAML 節點資料流，`x:Members`以名為`Members`，XAML 語言 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="bbcde-114">In a XAML node stream, `x:Members` is represented as a member named `Members`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="bbcde-115">成員`Members`包含唯讀的泛型清單`Member`物件。</span><span class="sxs-lookup"><span data-stu-id="bbcde-115">The member `Members` contains a read-only generic list of `Member` objects.</span></span> <span data-ttu-id="bbcde-116">在典型的標記中的個別成員指定為`x:Property`屬性項目。</span><span class="sxs-lookup"><span data-stu-id="bbcde-116">In typical markup the individual members are specified as `x:Property` property elements.</span></span> <span data-ttu-id="bbcde-117">`x:Property`更精確的型別，特別是針對類型的屬性，而指派給`x:Member`。</span><span class="sxs-lookup"><span data-stu-id="bbcde-117">`x:Property` is a more precise type specifically for properties of types and is assignable to `x:Member`.</span></span> <span data-ttu-id="bbcde-118">如需詳細資訊，請參閱[X:property 指示詞](../../../docs/framework/xaml-services/x-property-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="bbcde-118">For more information, see [x:Property Directive](../../../docs/framework/xaml-services/x-property-directive.md).</span></span>  
  
 <span data-ttu-id="bbcde-119">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="bbcde-119">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="bbcde-120">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="bbcde-120">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="bbcde-121">不過，.NET Framework XAML 服務層級不支援關聯類型與成員或產生動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="bbcde-121">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="bbcde-122">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="bbcde-122">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="bbcde-123">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="bbcde-123">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xmembers-for-windows-workflow-foundation"></a><span data-ttu-id="bbcde-124">X:members for Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="bbcde-124">x:Members for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="bbcde-125">針對 Windows Workflow Foundation，`x:Members`包含完全以 XAML 或 XAML 撰寫之自訂活動的成員 – 定義活動設計工具的程式碼後置的動態成員。</span><span class="sxs-lookup"><span data-stu-id="bbcde-125">For Windows Workflow Foundation, `x:Members` contains the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="bbcde-126">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="bbcde-126">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="bbcde-127">這不是 .NET Framework XAML 服務層級的需求，但是當 XAML 生產是由支援自訂活動和 Windows Workflow Foundation XAML 的 MSBUILD 建置動作載入時，通常會變成需求。</span><span class="sxs-lookup"><span data-stu-id="bbcde-127">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="bbcde-128">`x:Members`必須是第一個子元素中宣告物件項目的標記`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="bbcde-128">`x:Members` must be the first child element in markup of the object element that declares the `x:Class`.</span></span>
