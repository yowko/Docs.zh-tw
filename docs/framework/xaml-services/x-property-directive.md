---
title: x:Property 指示詞
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 34f982c30a345f95c7a1c7e70de8c5cc4de62cbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419769"
---
# <a name="xproperty-directive"></a><span data-ttu-id="4df6a-102">x:Property 指示詞</span><span class="sxs-lookup"><span data-stu-id="4df6a-102">x:Property Directive</span></span>
<span data-ttu-id="4df6a-103">在標記中宣告 XAML 屬性。</span><span class="sxs-lookup"><span data-stu-id="4df6a-103">Declares a XAML property in markup.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="4df6a-104">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="4df6a-104">XAML Object Element Usage</span></span>  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="4df6a-105">XAML 值</span><span class="sxs-lookup"><span data-stu-id="4df6a-105">XAML Values</span></span>  
  
|||  
|-|-|  
|`className`|<span data-ttu-id="4df6a-106">XAML 生產的支援類別或部分類別名稱。</span><span class="sxs-lookup"><span data-stu-id="4df6a-106">Name of the backing class or partial class for the XAML production.</span></span>|  
|`propertyName`|<span data-ttu-id="4df6a-107">正在定義之屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="4df6a-107">Member name of the property being defined.</span></span>|  
|`propertyType`|<span data-ttu-id="4df6a-108">指定這個屬性類型的類型名稱 (或其他特定架構的字串形式)。</span><span class="sxs-lookup"><span data-stu-id="4df6a-108">Type name (or other string form, framework-specific) that specifies the type of this property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df6a-109">備註</span><span class="sxs-lookup"><span data-stu-id="4df6a-109">Remarks</span></span>  
 <span data-ttu-id="4df6a-110">在 .NET Framework XAML 服務實作中，</span><span class="sxs-lookup"><span data-stu-id="4df6a-110">In the .NET Framework XAML Services implementation, .</span></span> <span data-ttu-id="4df6a-111">`x:Property` 沒有直接的類型支援，但受到 <xref:System.Windows.Markup.PropertyDefinition> 類別的支援。</span><span class="sxs-lookup"><span data-stu-id="4df6a-111">`x:Property` does not have a direct type backing, but is supported by the <xref:System.Windows.Markup.PropertyDefinition> class.</span></span> <span data-ttu-id="4df6a-112">在 XAML 節點資料流中，`x:Property` 項目會以 XAML 語言 XAML 命名空間中名為 `Property` 的成員表示。</span><span class="sxs-lookup"><span data-stu-id="4df6a-112">In a XAML node stream, an `x:Property` element is represented as a member named `Property`, from the XAML language XAML namespace.</span></span> <span data-ttu-id="4df6a-113">成員 `Property` 包含依標記宣告的屬性。</span><span class="sxs-lookup"><span data-stu-id="4df6a-113">The member `Property` hold attributes as declared by markup.</span></span>  
  
 <span data-ttu-id="4df6a-114">`Name` 和 `Type` 的意義不是在 .NET Framework XAML 服務層級上指派。</span><span class="sxs-lookup"><span data-stu-id="4df6a-114">The meaning of `Name` and `Type` are not assigned at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="4df6a-115">它們會在初始 XAML 節點資料流中儲存為字串值，以便稍後依據特定架構可能加諸的規則解譯。</span><span class="sxs-lookup"><span data-stu-id="4df6a-115">They are stored in the initial XAML node stream as string values, to be interpreted later under the rules that might be imposed by specific frameworks.</span></span> <span data-ttu-id="4df6a-116">這個意義可能與 XAML 名稱和 XAML 類型的意義一致，或可能只是在支援類型系統中有效，視實作而定。</span><span class="sxs-lookup"><span data-stu-id="4df6a-116">The meaning might align to a XAML name and XAML type meaning, or might only be valid in a backing type system, depending on the implementation.</span></span>  
  
 <span data-ttu-id="4df6a-117">若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="4df6a-117">To support a practical usage of `x:Members` as a means to specify member definitions in markup, the members must be associated with a class that can be modified.</span></span> <span data-ttu-id="4df6a-118">預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。</span><span class="sxs-lookup"><span data-stu-id="4df6a-118">The intended model is that `x:Members` exists as a member of a type that specifies an `x:Class`.</span></span> <span data-ttu-id="4df6a-119">不過，.NET Framework XAML 服務層級不支援關聯類型與成員或產生動態成員定義的機制。</span><span class="sxs-lookup"><span data-stu-id="4df6a-119">However, the mechanism for associating types and members or for producing dynamic member definitions is not supported at the .NET Framework XAML Services level.</span></span> <span data-ttu-id="4df6a-120">這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。</span><span class="sxs-lookup"><span data-stu-id="4df6a-120">This is left to individual frameworks that have application models that support member definitions from XAML.</span></span> <span data-ttu-id="4df6a-121">通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。</span><span class="sxs-lookup"><span data-stu-id="4df6a-121">Typically, MSBUILD build actions that markup-compile the XAML and either integrate it with code-behind or produce pure from-XAML assemblies are needed to support that feature.</span></span>  
  
## <a name="xproperty-for-windows-workflow-foundation"></a><span data-ttu-id="4df6a-122">Windows Workflow Foundation 的 x:Property</span><span class="sxs-lookup"><span data-stu-id="4df6a-122">x:Property for Windows Workflow Foundation</span></span>  
 <span data-ttu-id="4df6a-123">針對 Windows Workflow Foundation，`x:Property` 會定義完全以 XAML 撰寫之自訂活動的成員，或程式碼後置活動設計工具的 XAML 定義動態成員。</span><span class="sxs-lookup"><span data-stu-id="4df6a-123">For Windows Workflow Foundation, `x:Property` defines the members of a custom activity composed entirely in XAML, or XAML –defined dynamic members for an activity designer with code-behind.</span></span> <span data-ttu-id="4df6a-124">`x:Class` 也必須在 XAML 生產的根項目上指定。</span><span class="sxs-lookup"><span data-stu-id="4df6a-124">`x:Class` must also be specified on the root element of the XAML production.</span></span> <span data-ttu-id="4df6a-125">這不是 .NET Framework XAML 服務層級的需求，但是當 XAML 生產是由支援自訂活動和 Windows Workflow Foundation XAML 的 MSBUILD 建置動作載入時，通常會變成需求。</span><span class="sxs-lookup"><span data-stu-id="4df6a-125">This is not a requirement at the .NET Framework XAML Services level, but becomes a requirement when the XAML production is loaded by the MSBUILD build actions that support custom activities and Windows Workflow Foundation XAML in general.</span></span> <span data-ttu-id="4df6a-126">Windows Workflow Foundation 不會使用純 XAML 類型名稱做為其預定的值，如`x:Property``Type`屬性，然後改為使用此處未記載的慣例。</span><span class="sxs-lookup"><span data-stu-id="4df6a-126">Windows Workflow Foundation does not use the pure XAML type name as its intended value for the `x:Property` `Type` attribute, and instead uses a convention that is not documented here.</span></span> <span data-ttu-id="4df6a-127">如需詳細資訊，請參閱 <<c0> [ 動態活動建立](https://msdn.microsoft.com/library/dd807392.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4df6a-127">For more information, see [Dynamic Activity Creation](https://msdn.microsoft.com/library/dd807392.aspx).</span></span>
