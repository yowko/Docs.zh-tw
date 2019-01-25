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
ms.openlocfilehash: 67d699782cd2ce2b13e159d2b7218b4868a8794c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670923"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="14fa9-102">x:Subclass 指示詞</span><span class="sxs-lookup"><span data-stu-id="14fa9-102">x:Subclass Directive</span></span>
<span data-ttu-id="14fa9-103">修改 XAML 標記編譯行為時`x:Class`也會提供。</span><span class="sxs-lookup"><span data-stu-id="14fa9-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="14fa9-104">而不是建立部分類別為基礎`x:Class`，提供`x:Class`會建立為中繼類別，並提供衍生的類別然後是根據預期`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="14fa9-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="14fa9-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="14fa9-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="14fa9-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="14fa9-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="14fa9-107">Optional.</span></span> <span data-ttu-id="14fa9-108">指定 CLR 命名空間包含`classname`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="14fa9-109">如果`namespace`指定，則句點 （.） 分隔`namespace`和`classname`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="14fa9-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="14fa9-110">Required.</span></span> <span data-ttu-id="14fa9-111">指定的連接已載入的 XAML 和您程式碼後置的 XAML 的部分類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="14fa9-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="14fa9-112">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="14fa9-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="14fa9-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="14fa9-113">Optional.</span></span> <span data-ttu-id="14fa9-114">可能會不同於`namespace`如果每個命名空間可以解析其他。</span><span class="sxs-lookup"><span data-stu-id="14fa9-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="14fa9-115">指定 CLR 命名空間包含`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="14fa9-116">如果`subclassName`指定，則句點 （.） 分隔`subclassNamespace`和`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="14fa9-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="14fa9-117">Required.</span></span> <span data-ttu-id="14fa9-118">指定的子類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="14fa9-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="14fa9-119">相依性</span><span class="sxs-lookup"><span data-stu-id="14fa9-119">Dependencies</span></span>  
 <span data-ttu-id="14fa9-120">[X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)也必須提供相同的物件，而且該物件必須是 XAML 生產的根項目。</span><span class="sxs-lookup"><span data-stu-id="14fa9-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14fa9-121">備註</span><span class="sxs-lookup"><span data-stu-id="14fa9-121">Remarks</span></span>  
 <span data-ttu-id="14fa9-122">`x:Subclass` 使用方式，主要是用於不支援部分類別宣告的語言。</span><span class="sxs-lookup"><span data-stu-id="14fa9-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="14fa9-123">做為類別`x:Subclass`不能是巢狀的類別，和`x:Subclass`"Dependencies"區段中所述，必須指向根的物件。</span><span class="sxs-lookup"><span data-stu-id="14fa9-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="14fa9-124">否則，概念的意義`x:Subclass`未定義的.NET Framework XAML 服務實作。</span><span class="sxs-lookup"><span data-stu-id="14fa9-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="14fa9-125">這是因為.NET Framework XAML 服務的行為不會指定由哪一個 XAML 標記和備份程式碼連線的整體程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="14fa9-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="14fa9-126">實作的進一步概念的相關`x:Class`和`x:Subclass`所使用的程式設計模型或應用程式模型來定義如何連接 XAML 標記，編譯過的標記，並以 CLR 為基礎的程式碼後置的特定架構執行。</span><span class="sxs-lookup"><span data-stu-id="14fa9-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="14fa9-127">每個架構可能會有自己的建置動作可讓某些行為或必須包含在建置環境的特定元件。</span><span class="sxs-lookup"><span data-stu-id="14fa9-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="14fa9-128">在架構中，建置動作也有所不同，根據特定的 CLR 語言用於程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="14fa9-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="14fa9-129">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="14fa9-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="14fa9-130">`x:Subclass` 可以在頁面根或在<xref:System.Windows.Application>在應用程式定義中，已有根`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="14fa9-131">宣告`x:Subclass`以外的頁面或應用程式的根，或未指定任何項目上`x:Class`存在，會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="14fa9-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="14fa9-132">建立衍生類別可正確`x:Subclass`案例是相當複雜。</span><span class="sxs-lookup"><span data-stu-id="14fa9-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="14fa9-133">您可能需要檢查的中繼檔 （.g 標記編譯，其名稱中包含的.xaml 檔案名稱所產生您專案的 obj 資料夾中的資料檔案）。</span><span class="sxs-lookup"><span data-stu-id="14fa9-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="14fa9-134">這些中繼檔案可協助您判斷在編譯的應用程式中加入部分類別中的某些程式設計建構的原點。</span><span class="sxs-lookup"><span data-stu-id="14fa9-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="14fa9-135">在衍生類別中的事件處理常式必須是`internal override`(`Friend Overrides` Microsoft Visual Basic 中) 若要在編譯期間建立中繼類別中覆寫處理常式的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="14fa9-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="14fa9-136">否則，衍生的類別實作隱藏 （陰影） 的中繼類別實作，而且中繼類別處理常式不會叫用。</span><span class="sxs-lookup"><span data-stu-id="14fa9-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="14fa9-137">當您定義這兩`x:Class`並`x:Subclass`，您不需要提供任何實作類別所參考的`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="14fa9-138">您只需要為它命名，以透過`x:Class`屬性，讓編譯器有一些類別，它會建立在中繼檔 （編譯器不會選取預設的名稱在此情況下） 中的指引。</span><span class="sxs-lookup"><span data-stu-id="14fa9-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="14fa9-139">您可以賦予`x:Class`類別的實作; 不過，這不是使用這兩個的典型案例`x:Class`和`x:Subclass`。</span><span class="sxs-lookup"><span data-stu-id="14fa9-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14fa9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14fa9-140">See also</span></span>
- [<span data-ttu-id="14fa9-141">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="14fa9-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)
- [<span data-ttu-id="14fa9-142">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="14fa9-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
