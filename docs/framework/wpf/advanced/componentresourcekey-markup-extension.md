---
title: "ComponentResourceKey 標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7f959318c5991fea2df92ff8000e85345fb35ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="b16b4-102">ComponentResourceKey 標記延伸</span><span class="sxs-lookup"><span data-stu-id="b16b4-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="b16b4-103">定義和參考會從外部組件載入的資源索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b16b4-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="b16b4-104">這可讓組件，而不是類別或組件中的明確資源字典中指定的目標類型的資源查閱。</span><span class="sxs-lookup"><span data-stu-id="b16b4-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="b16b4-105">XAML 屬性使用方式 （設定索引鍵，compact）</span><span class="sxs-lookup"><span data-stu-id="b16b4-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="b16b4-106">XAML 屬性使用方式 （設定索引鍵、 詳細）</span><span class="sxs-lookup"><span data-stu-id="b16b4-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="b16b4-107">XAML 屬性使用方式 （提出要求的資源，compact）</span><span class="sxs-lookup"><span data-stu-id="b16b4-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="b16b4-108">XAML 屬性使用方式 （提出要求的資源，詳細資訊）</span><span class="sxs-lookup"><span data-stu-id="b16b4-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="b16b4-109">XAML 值</span><span class="sxs-lookup"><span data-stu-id="b16b4-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="b16b4-110">公開名稱[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]資源組件中定義的類型。</span><span class="sxs-lookup"><span data-stu-id="b16b4-110">The name of the public [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="b16b4-111">資源的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b16b4-111">The key for the resource.</span></span> <span data-ttu-id="b16b4-112">資源是在查閱，`targetID`會類似於[X:key 指示詞](../../../../docs/framework/xaml-services/x-key-directive.md)的資源。</span><span class="sxs-lookup"><span data-stu-id="b16b4-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b16b4-113">備註</span><span class="sxs-lookup"><span data-stu-id="b16b4-113">Remarks</span></span>  
 <span data-ttu-id="b16b4-114">上述的使用方式中所見 {`ComponentResourceKey`} 中兩個地方找到標記延伸使用方式：</span><span class="sxs-lookup"><span data-stu-id="b16b4-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
-   <span data-ttu-id="b16b4-115">內的主題資源字典，控制項作者所提供的索引鍵定義。</span><span class="sxs-lookup"><span data-stu-id="b16b4-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
-   <span data-ttu-id="b16b4-116">從組件存取佈景主題的資源，當您重製樣板控制項但想要使用來自所控制的主題提供資源的屬性值。</span><span class="sxs-lookup"><span data-stu-id="b16b4-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="b16b4-117">參考來自佈景主題的元件資源，建議您改用`{DynamicResource}`而不是`{StaticResource}`。</span><span class="sxs-lookup"><span data-stu-id="b16b4-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="b16b4-118">這是顯示在 使用方式。</span><span class="sxs-lookup"><span data-stu-id="b16b4-118">This is shown in the usages.</span></span> <span data-ttu-id="b16b4-119">`{DynamicResource}`建議，因為使用者可以變更本身的佈景主題。</span><span class="sxs-lookup"><span data-stu-id="b16b4-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="b16b4-120">如果您希望元件的資源最接近控制項作者的意圖支援佈景主題，您應該啟用您元件的資源參考也是動態。</span><span class="sxs-lookup"><span data-stu-id="b16b4-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="b16b4-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>識別存在於實際定義資源的目標組件的類型。</span><span class="sxs-lookup"><span data-stu-id="b16b4-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="b16b4-122">A`ComponentResourceKey`可以定義，以及使用獨立於完全瞭解其中<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>已定義，但最後必須解析參考的組件透過型別。</span><span class="sxs-lookup"><span data-stu-id="b16b4-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="b16b4-123">針對常見的用法<xref:System.Windows.ComponentResourceKey>是定義為類別的成員然後公開的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b16b4-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="b16b4-124">若是如此，您用於<xref:System.Windows.ComponentResourceKey>類別建構函式、 標記延伸。</span><span class="sxs-lookup"><span data-stu-id="b16b4-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="b16b4-125">如需詳細資訊，請參閱<xref:System.Windows.ComponentResourceKey>，或主題的 「 定義和參考索引鍵的主題資源 」 一節[控制項撰寫概觀](../../../../docs/framework/wpf/controls/control-authoring-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b16b4-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="b16b4-126">建立金鑰和參考做為索引鍵的資源，如屬性語法通常用於`ComponentResourceKey`標記延伸。</span><span class="sxs-lookup"><span data-stu-id="b16b4-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="b16b4-127">所顯示的精簡語法依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>建構函式簽章和標記延伸的位置參數用法。</span><span class="sxs-lookup"><span data-stu-id="b16b4-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="b16b4-128">順序`targetTypeName`和`targetID`會提供很重要。</span><span class="sxs-lookup"><span data-stu-id="b16b4-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="b16b4-129">詳細語法依賴<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>預設建構函式，然後按一下 設定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>類似於物件項目，則為 true 的屬性語法的方式。</span><span class="sxs-lookup"><span data-stu-id="b16b4-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType> default constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="b16b4-130">在詳細語法中，設定屬性的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="b16b4-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="b16b4-131">主題中的更多詳細資料中所述的關聯性和這些兩個替代方法 （compact 和詳細資訊） 的機制是[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="b16b4-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="b16b4-132">技術上來說，值`targetID`可以是任何物件，它不是字串。</span><span class="sxs-lookup"><span data-stu-id="b16b4-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="b16b4-133">不過，在 WPF 中最常見的用法是對齊`targetID`值與字串，而且在這類字串中是有效的表單[XamlName 文法](../../../../docs/framework/xaml-services/xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="b16b4-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="b16b4-134">`ComponentResourceKey`可用於物件項目語法。</span><span class="sxs-lookup"><span data-stu-id="b16b4-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="b16b4-135">在此情況下，指定的值都<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>和<xref:System.Windows.ComponentResourceKey.ResourceId%2A>來正確地初始化延伸的屬性必要項目。</span><span class="sxs-lookup"><span data-stu-id="b16b4-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="b16b4-136">在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器實作，這個標記延伸的處理由定義<xref:System.Windows.ComponentResourceKey>類別。</span><span class="sxs-lookup"><span data-stu-id="b16b4-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="b16b4-137">`ComponentResourceKey` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="b16b4-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="b16b4-138">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="b16b4-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="b16b4-139">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b16b4-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="b16b4-140">如需詳細資訊，請參閱[標記延伸和 WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="b16b4-140">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16b4-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b16b4-141">See Also</span></span>  
 <xref:System.Windows.ComponentResourceKey>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="b16b4-142">控制項撰寫概觀</span><span class="sxs-lookup"><span data-stu-id="b16b4-142">Control Authoring Overview</span></span>](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [<span data-ttu-id="b16b4-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="b16b4-143">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="b16b4-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="b16b4-144">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
