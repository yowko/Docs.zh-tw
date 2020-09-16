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
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540715"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="f4120-102">x:Subclass 指示詞</span><span class="sxs-lookup"><span data-stu-id="f4120-102">x:Subclass Directive</span></span>

<span data-ttu-id="f4120-103">當也提供時，修改 XAML 標記編譯行為 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="f4120-104">所提供的會以中繼類別的形式建立，而不是建立以中繼類別為基礎的部分類別 `x:Class` `x:Class` ，然後您所提供的衍生類別應該以作為基礎 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="f4120-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="f4120-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="f4120-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="f4120-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="f4120-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f4120-107">Optional.</span></span> <span data-ttu-id="f4120-108">指定包含的 CLR 命名空間 `classname` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="f4120-109">如果 `namespace` 指定了，就會以點 (。 ) 分隔 `namespace` 和 `classname` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="f4120-110">必要。</span><span class="sxs-lookup"><span data-stu-id="f4120-110">Required.</span></span> <span data-ttu-id="f4120-111">指定部分類別的 CLR 名稱，以連接載入的 XAML 和該 XAML 的程式碼後端。</span><span class="sxs-lookup"><span data-stu-id="f4120-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="f4120-112">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="f4120-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="f4120-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f4120-113">Optional.</span></span> <span data-ttu-id="f4120-114">`namespace`如果每個命名空間可以解析另一個命名空間，則可以不同。</span><span class="sxs-lookup"><span data-stu-id="f4120-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="f4120-115">指定包含的 CLR 命名空間 `subclassName` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="f4120-116">如果 `subclassName` 指定了，就會以點 (。 ) 分隔 `subclassNamespace` 和 `subclassName` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="f4120-117">必要。</span><span class="sxs-lookup"><span data-stu-id="f4120-117">Required.</span></span> <span data-ttu-id="f4120-118">指定子類別的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="f4120-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="f4120-119">相依性</span><span class="sxs-lookup"><span data-stu-id="f4120-119">Dependencies</span></span>

<span data-ttu-id="f4120-120">您也必須在相同的物件上提供[x：Class](xclass-directive.md)指示詞，且該物件必須是 XAML 生產的根項目。</span><span class="sxs-lookup"><span data-stu-id="f4120-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="f4120-121">備註</span><span class="sxs-lookup"><span data-stu-id="f4120-121">Remarks</span></span>

<span data-ttu-id="f4120-122">`x:Subclass` 使用方式主要適用于不支援部分類別宣告的語言。</span><span class="sxs-lookup"><span data-stu-id="f4120-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="f4120-123">用作的類別 `x:Subclass` 不能是嵌套類別，而且 `x:Subclass` 必須參考根物件，如「相依性」一節中所述。</span><span class="sxs-lookup"><span data-stu-id="f4120-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="f4120-124">否則， `x:Subclass` .NET XAML 服務執行會未定義的概念意義。</span><span class="sxs-lookup"><span data-stu-id="f4120-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="f4120-125">這是因為 .NET XAML 服務的行為不會指定 XAML 標記和支援的程式碼所連接的整體程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="f4120-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="f4120-126">與和相關的進一步概念 `x:Class` 的 `x:Subclass` 執行是由使用程式設計模型或應用程式模型的特定架構所執行，以定義如何連接 XAML 標記、編譯的標記和 CLR 程式碼後端。</span><span class="sxs-lookup"><span data-stu-id="f4120-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="f4120-127">每個架構都可能有自己的組建動作，可啟用某些行為，或是必須包含在組建環境中的特定元件。</span><span class="sxs-lookup"><span data-stu-id="f4120-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="f4120-128">在架構中，組建動作也會根據用於程式碼後端的特定 CLR 語言而有所不同。</span><span class="sxs-lookup"><span data-stu-id="f4120-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="f4120-129">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="f4120-129">WPF Usage Notes</span></span>

<span data-ttu-id="f4120-130">`x:Subclass` 可以位於頁面根目錄或 <xref:System.Windows.Application> 應用程式定義的根目錄中，也就是已有的應用程式定義 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="f4120-131">`x:Subclass`在頁面或應用程式根目錄以外的任何專案上宣告，或指定不存在的專案 `x:Class` ，會導致編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="f4120-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="f4120-132">建立適用于此案例的衍生類別 `x:Subclass` 相當複雜。</span><span class="sxs-lookup"><span data-stu-id="f4120-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="f4120-133">您可能需要檢查中繼檔案， (專案的 obj 資料夾中所產生的. g 檔案，其名稱包含) 的 .xaml 檔案名。</span><span class="sxs-lookup"><span data-stu-id="f4120-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="f4120-134">這些中繼檔案可協助您在已編譯的應用程式中，于聯結的部分類別中判斷特定程式設計結構的來源。</span><span class="sxs-lookup"><span data-stu-id="f4120-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="f4120-135">衍生類別中的事件處理常式必須 `internal override` `Friend Overrides` 在 Microsoft Visual Basic) 中 (，才能覆寫在編譯期間于中繼類別中建立之處理常式的存根。</span><span class="sxs-lookup"><span data-stu-id="f4120-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="f4120-136">否則，衍生類別實 (會隱藏中繼類別實) 陰影，而不會叫用中繼類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="f4120-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="f4120-137">當您同時定義 `x:Class` 和時 `x:Subclass` ，您不需要為所參考的類別提供任何實作為 `x:Class` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="f4120-138">您只需要透過屬性提供它的名稱， `x:Class` 編譯器就會在中繼檔案中建立類別的指引， (編譯器不會在此情況下選取預設名稱) 。</span><span class="sxs-lookup"><span data-stu-id="f4120-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="f4120-139">您可以為 `x:Class` 類別提供實值; 不過，這不是使用和的一般案例 `x:Class` `x:Subclass` 。</span><span class="sxs-lookup"><span data-stu-id="f4120-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4120-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4120-140">See also</span></span>

- [<span data-ttu-id="f4120-141">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="f4120-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="f4120-142">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="f4120-142">XAML and Custom Classes for WPF</span></span>](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
