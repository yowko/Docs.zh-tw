---
title: ComponentResourceKey 標記延伸
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243358"
---
# <a name="componentresourcekey-markup-extension"></a><span data-ttu-id="77514-102">ComponentResourceKey 標記延伸</span><span class="sxs-lookup"><span data-stu-id="77514-102">ComponentResourceKey Markup Extension</span></span>
<span data-ttu-id="77514-103">定義和引用從外部程式集載入的資源的鍵。</span><span class="sxs-lookup"><span data-stu-id="77514-103">Defines and references keys for resources that are loaded from external assemblies.</span></span> <span data-ttu-id="77514-104">這使資源查找能夠在程式集中指定目標類型,而不是在程式集或類上指定顯式資源字典。</span><span class="sxs-lookup"><span data-stu-id="77514-104">This enables a resource lookup to specify a target type in an assembly, rather than an explicit resource dictionary in an assembly or on a class.</span></span>  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a><span data-ttu-id="77514-105">XAML 屬性用法(設定鍵,緊湊)</span><span class="sxs-lookup"><span data-stu-id="77514-105">XAML Attribute Usage (setting key, compact)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a><span data-ttu-id="77514-106">XAML 屬性用法(設定鍵,詳細)</span><span class="sxs-lookup"><span data-stu-id="77514-106">XAML Attribute Usage (setting key, verbose)</span></span>  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a><span data-ttu-id="77514-107">XAML 屬性使用(請求資源,緊湊)</span><span class="sxs-lookup"><span data-stu-id="77514-107">XAML Attribute Usage (requesting resource, compact)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a><span data-ttu-id="77514-108">XAML 屬性使用(請求資源,詳細)</span><span class="sxs-lookup"><span data-stu-id="77514-108">XAML Attribute Usage (requesting resource, verbose)</span></span>  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="77514-109">XAML 值</span><span class="sxs-lookup"><span data-stu-id="77514-109">XAML Values</span></span>  
  
|||  
|-|-|  
|`targetTypeName`|<span data-ttu-id="77514-110">在資源程式集中定義的公共通用語言運行時 (CLR) 類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="77514-110">The name of the public common language runtime (CLR) type that is defined in the resource assembly.</span></span>|  
|`targetID`|<span data-ttu-id="77514-111">資源的鍵。</span><span class="sxs-lookup"><span data-stu-id="77514-111">The key for the resource.</span></span> <span data-ttu-id="77514-112">當資源被抬起來時`targetID`,將類似於資源的[x:Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="77514-112">When resources are looked up, `targetID` will be analogous to the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) of the resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77514-113">備註</span><span class="sxs-lookup"><span data-stu-id="77514-113">Remarks</span></span>  
 <span data-ttu-id="77514-114">如上文用法所示,在以下兩`ComponentResourceKey`個位置可以找到 [ 標記延伸用法:</span><span class="sxs-lookup"><span data-stu-id="77514-114">As seen in the usages above, a {`ComponentResourceKey`} markup extension usage is found in two places:</span></span>  
  
- <span data-ttu-id="77514-115">主題資源字典中鍵的定義,由控件作者提供。</span><span class="sxs-lookup"><span data-stu-id="77514-115">The definition of a key within a theme resource dictionary, as provided by a control author.</span></span>  
  
- <span data-ttu-id="77514-116">從程式集存取主題資源時,當您重新範本化控制項,但希望使用來自控制項主題提供的資源的屬性值時。</span><span class="sxs-lookup"><span data-stu-id="77514-116">Accessing a theme resource from the assembly, when you are retemplating the control but want to use property values that come from resources provided by the control's themes.</span></span>  
  
 <span data-ttu-id="77514-117">對於參考來自主題的元件資源,通常建議您使用`{DynamicResource}`而不是`{StaticResource}`。</span><span class="sxs-lookup"><span data-stu-id="77514-117">For referencing component resources that come from themes, it is generally recommended that you use `{DynamicResource}` rather than `{StaticResource}`.</span></span> <span data-ttu-id="77514-118">這在用法中顯示。</span><span class="sxs-lookup"><span data-stu-id="77514-118">This is shown in the usages.</span></span> <span data-ttu-id="77514-119">`{DynamicResource}`建議使用,因為使用者可以更改主題本身。</span><span class="sxs-lookup"><span data-stu-id="77514-119">`{DynamicResource}` is recommended because the theme itself can be changed by the user.</span></span> <span data-ttu-id="77514-120">如果希望與控制項作者支援主題的意圖最匹配的元件資源,則應使元件資源引用也是動態的。</span><span class="sxs-lookup"><span data-stu-id="77514-120">If you want the component resource that most closely matches the control author's intent for supporting a theme, you should enable your component resource reference to be dynamic also.</span></span>  
  
 <span data-ttu-id="77514-121"><xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>標識目標程式集中存在的類型,其中實際定義了資源。</span><span class="sxs-lookup"><span data-stu-id="77514-121">The <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> identifies a type that exists in the target assembly where the resource is actually defined.</span></span> <span data-ttu-id="77514-122">`ComponentResourceKey`可以定義和使用,而確切知道定義<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>的位置 ,但最終必須通過引用的程式集解析類型。</span><span class="sxs-lookup"><span data-stu-id="77514-122">A `ComponentResourceKey` can be defined and used independently of knowing exactly where the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> is defined, but eventually must resolve the type through referenced assemblies.</span></span>  
  
 <span data-ttu-id="77514-123">一個常用法<xref:System.Windows.ComponentResourceKey>種是定義密鑰,然後作為類的成員公開。</span><span class="sxs-lookup"><span data-stu-id="77514-123">A common usage for <xref:System.Windows.ComponentResourceKey> is to define keys that are then exposed as members of a class.</span></span> <span data-ttu-id="77514-124">對於此用法,<xref:System.Windows.ComponentResourceKey>請使用類建構函數,而不是標記副檔名。</span><span class="sxs-lookup"><span data-stu-id="77514-124">For this usage, you use the <xref:System.Windows.ComponentResourceKey> class constructor, not the markup extension.</span></span> <span data-ttu-id="77514-125">有關詳細資訊,請參閱<xref:System.Windows.ComponentResourceKey>主題[「控件創作概述](../controls/control-authoring-overview.md)」中的「主題資源定義和引用鍵」部分。</span><span class="sxs-lookup"><span data-stu-id="77514-125">For more information, see <xref:System.Windows.ComponentResourceKey>, or the "Defining and Referencing Keys for Theme Resources" section of the topic [Control Authoring Overview](../controls/control-authoring-overview.md).</span></span>  
  
 <span data-ttu-id="77514-126">對於建立鍵和引用鍵控資源,屬性語法通常用於`ComponentResourceKey`標記擴展。</span><span class="sxs-lookup"><span data-stu-id="77514-126">For both establishing keys and referencing keyed resources, attribute syntax is commonly used for the `ComponentResourceKey` markup extension.</span></span>  
  
 <span data-ttu-id="77514-127">顯示的緊湊語法依賴於標記擴展<xref:System.Windows.ComponentResourceKey.%23ctor%2A>的構造函數簽名和位置參數用法。</span><span class="sxs-lookup"><span data-stu-id="77514-127">The compact syntax shown relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> constructor signature and positional parameter usage of a markup extension.</span></span> <span data-ttu-id="77514-128">`targetTypeName`給出的順序`targetID`很重要。</span><span class="sxs-lookup"><span data-stu-id="77514-128">The order in which the `targetTypeName` and `targetID` are given is important.</span></span> <span data-ttu-id="77514-129">詳細語法依賴於無<xref:System.Windows.ComponentResourceKey.%23ctor%2A>參數構造函數,然後以類似於物件元素上的真實<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>屬性<xref:System.Windows.ComponentResourceKey.ResourceId%2A>語法 的方式設置 和。</span><span class="sxs-lookup"><span data-stu-id="77514-129">The verbose syntax relies on the <xref:System.Windows.ComponentResourceKey.%23ctor%2A> parameterless constructor, and then sets the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> in a way that is analogous to a true attribute syntax on an object element.</span></span> <span data-ttu-id="77514-130">在詳細語法中,屬性的設置順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="77514-130">In the verbose syntax, the order in which the properties are set is not important.</span></span> <span data-ttu-id="77514-131">這兩種備選方案的關係和機制(緊湊和詳細)在主題[標記擴展和WPF XAML](markup-extensions-and-wpf-xaml.md)中進行了更詳細的描述。</span><span class="sxs-lookup"><span data-stu-id="77514-131">The relationship and mechanisms of these two alternatives (compact and verbose) is described in more detail in the topic [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="77514-132">從技術上講,的值`targetID`可以是任何物件,它不必是字串。</span><span class="sxs-lookup"><span data-stu-id="77514-132">Technically, the value for `targetID` can be any object, it does not have to be a string.</span></span> <span data-ttu-id="77514-133">但是,WPF 中最常見的用法是`targetID`使 值與字串的窗體對齊,以及此類字串在[XamlName 語法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)中有效的位置。</span><span class="sxs-lookup"><span data-stu-id="77514-133">However, the most common usage in WPF is to align the `targetID` value with forms that are strings, and where such strings are valid in the [XamlName Grammar](../../../desktop-wpf/xaml-services/xamlname-grammar.md).</span></span>  
  
 <span data-ttu-id="77514-134">`ComponentResourceKey`可用於物件元素語法。</span><span class="sxs-lookup"><span data-stu-id="77514-134">`ComponentResourceKey` can be used in object element syntax.</span></span> <span data-ttu-id="77514-135">在這種情況下,需要指定<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A><xref:System.Windows.ComponentResourceKey.ResourceId%2A>和屬性的值才能正確初始化擴展。</span><span class="sxs-lookup"><span data-stu-id="77514-135">In this case, specifying the value of both the <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> and <xref:System.Windows.ComponentResourceKey.ResourceId%2A> properties is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="77514-136">讀[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]取器實現中,此標記擴展的處理由<xref:System.Windows.ComponentResourceKey>類定義。</span><span class="sxs-lookup"><span data-stu-id="77514-136">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader implementation, the handling for this markup extension is defined by the <xref:System.Windows.ComponentResourceKey> class.</span></span>  
  
 <span data-ttu-id="77514-137">`ComponentResourceKey` 是一種標記延伸。</span><span class="sxs-lookup"><span data-stu-id="77514-137">`ComponentResourceKey` is a markup extension.</span></span> <span data-ttu-id="77514-138">如果必須將屬性 (Attribute) 值加上逸出符號，以免成為常值或處理常式名稱，而且這個動作必須更全面地實施 (而不是只對特定類型或屬性 (Property) 設定類型轉換子 (Type Converter))，則通常會實作標記延伸。</span><span class="sxs-lookup"><span data-stu-id="77514-138">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="77514-139">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的所有標記延伸都會在其屬性語法中使用 { 與 } 字元，這個慣例讓 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器知道某個標記延伸必須處理這個屬性。</span><span class="sxs-lookup"><span data-stu-id="77514-139">All markup extensions in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] use the { and } characters in their attribute syntax, which is the convention by which a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="77514-140">如需詳細資訊，請參閱[標記延伸和 WPF XAML](markup-extensions-and-wpf-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="77514-140">For more information, see [Markup Extensions and WPF XAML](markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77514-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77514-141">See also</span></span>

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="77514-142">控制項撰寫概觀</span><span class="sxs-lookup"><span data-stu-id="77514-142">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
- [<span data-ttu-id="77514-143">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="77514-143">XAML Overview (WPF)</span></span>](../../../desktop-wpf/fundamentals/xaml.md)
- [<span data-ttu-id="77514-144">標記延伸和 WPF XAML</span><span class="sxs-lookup"><span data-stu-id="77514-144">Markup Extensions and WPF XAML</span></span>](markup-extensions-and-wpf-xaml.md)
