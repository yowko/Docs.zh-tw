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
ms.openlocfilehash: b04982ff0b7685b4e4b809255e3bbe541b42cb9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566414"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="575f8-102">x:Subclass 指示詞</span><span class="sxs-lookup"><span data-stu-id="575f8-102">x:Subclass Directive</span></span>
<span data-ttu-id="575f8-103">修改 XAML 標記編譯行為時`x:Class`也會提供。</span><span class="sxs-lookup"><span data-stu-id="575f8-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="575f8-104">而不是建立部分類別，根據`x:Class`，提供`x:Class`建立為中繼類別，而且應該然後根據您提供的衍生的類別`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="575f8-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="575f8-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="575f8-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="575f8-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="575f8-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`namespace`|<span data-ttu-id="575f8-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="575f8-107">Optional.</span></span> <span data-ttu-id="575f8-108">指定 CLR 命名空間包含`classname`。</span><span class="sxs-lookup"><span data-stu-id="575f8-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="575f8-109">如果`namespace`指定，則句點 （.） 分隔`namespace`和`classname`。</span><span class="sxs-lookup"><span data-stu-id="575f8-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|  
|`classname`|<span data-ttu-id="575f8-110">必要。</span><span class="sxs-lookup"><span data-stu-id="575f8-110">Required.</span></span> <span data-ttu-id="575f8-111">指定連接載入的 XAML 和程式碼後置該 XAML 的部分類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="575f8-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="575f8-112">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="575f8-112">See Remarks.</span></span>|  
|`subclassNamespace`|<span data-ttu-id="575f8-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="575f8-113">Optional.</span></span> <span data-ttu-id="575f8-114">可能會不同於`namespace`如果每個命名空間可以解析其他。</span><span class="sxs-lookup"><span data-stu-id="575f8-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="575f8-115">指定 CLR 命名空間包含`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="575f8-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="575f8-116">如果`subclassName`指定，則句點 （.） 分隔`subclassNamespace`和`subclassName`。</span><span class="sxs-lookup"><span data-stu-id="575f8-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|  
|`subclassName`|<span data-ttu-id="575f8-117">必要。</span><span class="sxs-lookup"><span data-stu-id="575f8-117">Required.</span></span> <span data-ttu-id="575f8-118">指定子類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="575f8-118">Specifies the CLR name of the subclass.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="575f8-119">相依性</span><span class="sxs-lookup"><span data-stu-id="575f8-119">Dependencies</span></span>  
 <span data-ttu-id="575f8-120">[X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)也必須提供相同的物件，而該物件必須是在 XAML 生產的根項目。</span><span class="sxs-lookup"><span data-stu-id="575f8-120">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="575f8-121">備註</span><span class="sxs-lookup"><span data-stu-id="575f8-121">Remarks</span></span>  
 <span data-ttu-id="575f8-122">`x:Subclass` 使用主要用於不支援部分類別宣告的語言。</span><span class="sxs-lookup"><span data-stu-id="575f8-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>  
  
 <span data-ttu-id="575f8-123">做為類別`x:Subclass`不可為巢狀的類別，和`x:Subclass`必須參考根物件 「 相依性 」 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="575f8-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>  
  
 <span data-ttu-id="575f8-124">否則，概念的意義`x:Subclass`未定義的.NET Framework XAML 服務實作。</span><span class="sxs-lookup"><span data-stu-id="575f8-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET Framework XAML Services implementation.</span></span> <span data-ttu-id="575f8-125">這是因為.NET Framework XAML 服務的行為未指定的 xaml 標記和支援的程式碼已連線的整體程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="575f8-125">This is because .NET Framework XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="575f8-126">與相關的進一步概念實作`x:Class`和`x:Subclass`都是透過使用的程式設計模型或應用程式模型來定義如何連接 XAML 標記、 編譯的標記，並以 CLR 為基礎的程式碼後置的特定架構。</span><span class="sxs-lookup"><span data-stu-id="575f8-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="575f8-127">每個架構可能會有自己啟用的某些行為或在建置環境中必須包含的特定元件的建置動作。</span><span class="sxs-lookup"><span data-stu-id="575f8-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="575f8-128">在架構中，建置動作各有不同，根據特定 CLR 語言用於程式碼後置。</span><span class="sxs-lookup"><span data-stu-id="575f8-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="575f8-129">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="575f8-129">WPF Usage Notes</span></span>  
 <span data-ttu-id="575f8-130">`x:Subclass` 可以是頁面根或<xref:System.Windows.Application>在應用程式定義中，已經有根`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="575f8-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="575f8-131">宣告`x:Subclass`網頁或應用程式的根目錄，或未指定它以外的任何項目上`x:Class`存在，會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="575f8-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>  
  
 <span data-ttu-id="575f8-132">建立衍生類別是否正確地為該工作`x:Subclass`案例是相當複雜。</span><span class="sxs-lookup"><span data-stu-id="575f8-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="575f8-133">您可能需要檢查中繼檔 （在 obj 資料夾，您的專案中編譯標記，其名稱中包含的.xaml 檔案名稱所產生的.g 檔案）。</span><span class="sxs-lookup"><span data-stu-id="575f8-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="575f8-134">這些中繼檔可協助您判斷在已編譯的應用程式中加入部分類別中的特定程式設計建構的來源。</span><span class="sxs-lookup"><span data-stu-id="575f8-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>  
  
 <span data-ttu-id="575f8-135">在衍生類別中的事件處理常式必須是`internal override`(`Friend Overrides`在 Microsoft Visual Basic) 才能在編譯期間建立中繼類別中覆寫針對此處理常式的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="575f8-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="575f8-136">否則衍生的類別實作會隱藏 （陰影） 的中繼類別實作，而且不會叫用的中繼類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="575f8-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>  
  
 <span data-ttu-id="575f8-137">當您同時定義`x:Class`和`x:Subclass`，您不需要提供任何實作類別所參考的`x:Class`。</span><span class="sxs-lookup"><span data-stu-id="575f8-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="575f8-138">您只需要提供給它透過名稱`x:Class`屬性，讓編譯器在有一些指導方針所建立的中繼檔案 （編譯器不會選取預設名稱在此情況下） 的類別。</span><span class="sxs-lookup"><span data-stu-id="575f8-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="575f8-139">您可以提供`x:Class`類別的實作; 不過，這不使用這兩個的典型範例`x:Class`和`x:Subclass`。</span><span class="sxs-lookup"><span data-stu-id="575f8-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575f8-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="575f8-140">See Also</span></span>  
 [<span data-ttu-id="575f8-141">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="575f8-141">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="575f8-142">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="575f8-142">XAML and Custom Classes for WPF</span></span>](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
