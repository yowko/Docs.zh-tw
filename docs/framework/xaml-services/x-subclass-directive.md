---
title: x:Subclass 指示詞
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053903"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="df752-102">x:Subclass 指示詞</span><span class="sxs-lookup"><span data-stu-id="df752-102">x:Subclass Directive</span></span>
<span data-ttu-id="df752-103">當同時提供時`x:Class` ，修改 XAML 標記編譯行為。</span><span class="sxs-lookup"><span data-stu-id="df752-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="df752-104">除了建立以為基礎`x:Class`的部分類別，提供`x:Class`的會建立為中繼類別，然後您所提供的衍生類別`x:Class`應該會以為基礎。</span><span class="sxs-lookup"><span data-stu-id="df752-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="df752-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="df752-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="df752-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="df752-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="df752-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df752-107">Optional.</span></span> <span data-ttu-id="df752-108">指定包含`classname`的 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="df752-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="df752-109">如果`namespace`指定了, 則句點 (.) 會`namespace`分隔`classname`和。</span><span class="sxs-lookup"><span data-stu-id="df752-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="df752-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="df752-110">Required.</span></span> <span data-ttu-id="df752-111">指定部分類別的 CLR 名稱, 此元件會連接已載入的 XAML 和該 XAML 的程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="df752-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="df752-112">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="df752-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="df752-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="df752-113">Optional.</span></span> <span data-ttu-id="df752-114">如果每個命名`namespace`空間都可以解析另一個，則可以與不同。</span><span class="sxs-lookup"><span data-stu-id="df752-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="df752-115">指定包含`subclassName`的 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="df752-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="df752-116">如果`subclassName`指定了, 則句點 (.) 會`subclassNamespace`分隔`subclassName`和。</span><span class="sxs-lookup"><span data-stu-id="df752-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="df752-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="df752-117">Required.</span></span> <span data-ttu-id="df752-118">指定子類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="df752-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="df752-119">相依性</span><span class="sxs-lookup"><span data-stu-id="df752-119">Dependencies</span></span>  
 <span data-ttu-id="df752-120">您也必須在相同的物件上提供[x：Class](x-class-directive.md)指示詞，而且該物件必須是 XAML 生產的根項目。</span><span class="sxs-lookup"><span data-stu-id="df752-120">[x:Class Directive](x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df752-121">備註</span><span class="sxs-lookup"><span data-stu-id="df752-121">Remarks</span></span>  
 <span data-ttu-id="df752-122">`x:Subclass`使用方式主要適用于不支援部分類別宣告的語言。</span><span class="sxs-lookup"><span data-stu-id="df752-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="df752-123">當做使用`x:Subclass`的類別不可以是嵌套類別，而且`x:Subclass`必須參考根物件，如「相依性」一節中所述。</span><span class="sxs-lookup"><span data-stu-id="df752-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="df752-124">否則，的概念意義`x:Subclass`會由 .NET Framework XAML 服務執行而未定義。</span><span class="sxs-lookup"><span data-stu-id="df752-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="df752-125">這是因為 .NET Framework XAML 服務行為並不會指定用來連接 XAML 標記和支援程式碼的整體程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="df752-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="df752-126">與`x:Class` 和`x:Subclass`相關的進一步概念的執行，是由使用程式設計模型或應用程式模型的特定架構，來定義如何連接 XAML 標記、編譯的標記和 CLR 程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="df752-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="df752-127">每個架構可能會有自己的組建動作，以啟用某些行為，或必須包含在組建環境中的特定元件。</span><span class="sxs-lookup"><span data-stu-id="df752-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="df752-128">在架構中，組建動作也會根據程式碼後置所使用的特定 CLR 語言而有所不同。</span><span class="sxs-lookup"><span data-stu-id="df752-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="df752-129">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="df752-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="df752-130">`x:Subclass`可以在頁面根目錄或應用程式定義中<xref:System.Windows.Application>的根目錄上，也就是已經有`x:Class`的。</span><span class="sxs-lookup"><span data-stu-id="df752-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="df752-131">在頁面或應用程式根目錄以外的任何專案上宣告，或指定不`x:Class`存在的專案，會導致編譯時期錯誤。 `x:Subclass`</span><span class="sxs-lookup"><span data-stu-id="df752-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="df752-132">建立可針對`x:Subclass`案例正常運作的衍生類別，相當複雜。</span><span class="sxs-lookup"><span data-stu-id="df752-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="df752-133">您可能需要檢查中繼檔案（在專案的 [obj] 資料夾中，透過標記編譯產生的. g 檔案，其中包含包含 .xaml 檔案名的名稱）。</span><span class="sxs-lookup"><span data-stu-id="df752-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="df752-134">這些中繼檔案可協助您判斷已編譯應用程式的聯結部分類別中，特定程式設計結構的來源。</span><span class="sxs-lookup"><span data-stu-id="df752-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="df752-135">衍生類別中的事件處理常式必須`internal override`是`Friend Overrides` （在 Microsoft Visual Basic 中），才能覆寫在編譯期間，在中繼類別中建立之處理常式的 stub。</span><span class="sxs-lookup"><span data-stu-id="df752-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="df752-136">否則，衍生的類別會隱藏（陰影）中繼類別的執行，而且不會叫用中繼類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="df752-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="df752-137">當您同時`x:Class`定義和`x:Subclass`時，您不需要為所參考的`x:Class`類別提供任何實作為。</span><span class="sxs-lookup"><span data-stu-id="df752-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="df752-138">您只需要透過`x:Class`屬性指定名稱，編譯器就會針對它在中繼檔案中建立的類別提供一些指引（在此案例中，編譯器不會選取預設名稱）。</span><span class="sxs-lookup"><span data-stu-id="df752-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="df752-139">您可以為`x:Class`類別提供一個實作為，不過，這不是`x:Class`使用和`x:Subclass`的一般案例。</span><span class="sxs-lookup"><span data-stu-id="df752-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df752-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df752-140">See also</span></span>

- [<span data-ttu-id="df752-141">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="df752-141">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="df752-142">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="df752-142">XAML and Custom Classes for WPF</span></span>](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
