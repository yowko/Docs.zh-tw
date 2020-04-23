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
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071364"
---
# <a name="xsubclass-directive"></a><span data-ttu-id="29c58-102">x:Subclass 指示詞</span><span class="sxs-lookup"><span data-stu-id="29c58-102">x:Subclass Directive</span></span>

<span data-ttu-id="29c58-103">在提供時`x:Class`修改 XAML 標記編譯行為。</span><span class="sxs-lookup"><span data-stu-id="29c58-103">Modifies XAML markup compile behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="29c58-104">提供的派生類應基於`x:Class``x:Class``x:Class`,而不是創建基於 的部分類。</span><span class="sxs-lookup"><span data-stu-id="29c58-104">Instead of creating a partial class that is based on `x:Class`, the provided `x:Class` is created as an intermediate class, and then your provided derived class is expected to be based on `x:Class`.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="29c58-105">XAML Attribute Usage</span><span class="sxs-lookup"><span data-stu-id="29c58-105">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="29c58-106">XAML 值</span><span class="sxs-lookup"><span data-stu-id="29c58-106">XAML Values</span></span>

|||
|-|-|
|`namespace`|<span data-ttu-id="29c58-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="29c58-107">Optional.</span></span> <span data-ttu-id="29c58-108">指定包含的`classname`CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="29c58-108">Specifies a CLR namespace that contains `classname`.</span></span> <span data-ttu-id="29c58-109">如果`namespace`指定,點 (.) 會`namespace`分`classname`隔與 。</span><span class="sxs-lookup"><span data-stu-id="29c58-109">If `namespace` is specified, a dot (.) separates `namespace` and `classname`.</span></span>|
|`classname`|<span data-ttu-id="29c58-110">必要。</span><span class="sxs-lookup"><span data-stu-id="29c58-110">Required.</span></span> <span data-ttu-id="29c58-111">指定連接載入的 XAML 和該 XAML 的代碼後面的部分類的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="29c58-111">Specifies the CLR name of the partial class that connects the loaded XAML and your code-behind for that XAML.</span></span> <span data-ttu-id="29c58-112">請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="29c58-112">See Remarks.</span></span>|
|`subclassNamespace`|<span data-ttu-id="29c58-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="29c58-113">Optional.</span></span> <span data-ttu-id="29c58-114">可以不同於`namespace`如果每個命名空間可以解析另一個。</span><span class="sxs-lookup"><span data-stu-id="29c58-114">Can be different from `namespace` if each namespace can resolve the other.</span></span> <span data-ttu-id="29c58-115">指定包含的`subclassName`CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="29c58-115">Specifies a CLR namespace that contains `subclassName`.</span></span> <span data-ttu-id="29c58-116">如果`subclassName`指定,點 (.) 會`subclassNamespace`分`subclassName`隔與 。</span><span class="sxs-lookup"><span data-stu-id="29c58-116">If `subclassName` is specified, a dot (.) separates `subclassNamespace` and `subclassName`.</span></span>|
|`subclassName`|<span data-ttu-id="29c58-117">必要。</span><span class="sxs-lookup"><span data-stu-id="29c58-117">Required.</span></span> <span data-ttu-id="29c58-118">指定子類的 CLR 名稱。</span><span class="sxs-lookup"><span data-stu-id="29c58-118">Specifies the CLR name of the subclass.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="29c58-119">相依性</span><span class="sxs-lookup"><span data-stu-id="29c58-119">Dependencies</span></span>

<span data-ttu-id="29c58-120">[x:類指令](xclass-directive.md)也必須在同一物件上提供,並且該物件必須是 XAML 生產的根元素。</span><span class="sxs-lookup"><span data-stu-id="29c58-120">[x:Class Directive](xclass-directive.md) must also be provided on the same object, and that object must be the root element of the XAML production.</span></span>

## <a name="remarks"></a><span data-ttu-id="29c58-121">備註</span><span class="sxs-lookup"><span data-stu-id="29c58-121">Remarks</span></span>

<span data-ttu-id="29c58-122">`x:Subclass`主要用於不支援部分類聲明的語言。</span><span class="sxs-lookup"><span data-stu-id="29c58-122">`x:Subclass` usage is primarily intended for languages that do not support partial class declarations.</span></span>

<span data-ttu-id="29c58-123">用作`x:Subclass`的 類不能是嵌套類,`x:Subclass`並且必須引用根物件,如"依賴"部分中所述。</span><span class="sxs-lookup"><span data-stu-id="29c58-123">The class used as the `x:Subclass` cannot be a nested class, and `x:Subclass` must refer to the root object as explained in the "Dependencies" section.</span></span>

<span data-ttu-id="29c58-124">否則,.NET XAML 服務實現未`x:Subclass`定義 其概念含義。</span><span class="sxs-lookup"><span data-stu-id="29c58-124">Otherwise, the conceptual meaning of `x:Subclass` is undefined by a .NET XAML Services implementation.</span></span> <span data-ttu-id="29c58-125">這是因為 .NET XAML 服務行為未指定連接 XAML 標記和背碼的總體程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="29c58-125">This is because .NET XAML Services behavior does not specify the overall programming model by which XAML markup and backing code are connected.</span></span> <span data-ttu-id="29c58-126">與`x:Class`和`x:Subclass`相關的其他概念的實現由使用程式設計模型或應用程式模型來定義如何連接 XAML 標記、編譯標記和基於 CLR 的代碼後面的特定框架執行。</span><span class="sxs-lookup"><span data-stu-id="29c58-126">Implementations of further concepts related to `x:Class` and `x:Subclass` are performed by specific frameworks that use programming models or application models to define how to connect XAML markup, compiled markup, and CLR-based code-behind.</span></span> <span data-ttu-id="29c58-127">每個框架可能都有自己的生成操作,這些操作啟用某些行為或必須包含在生成環境中的特定元件。</span><span class="sxs-lookup"><span data-stu-id="29c58-127">Each framework might have its own build actions that enable some of the behavior, or specific components that must be included in the build environment.</span></span> <span data-ttu-id="29c58-128">在框架中,生成操作還可以根據用於代碼後面的特定 CLR 語言而變化。</span><span class="sxs-lookup"><span data-stu-id="29c58-128">Within a framework, build actions can also vary based on the specific CLR language that is used for the code-behind.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="29c58-129">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="29c58-129">WPF Usage Notes</span></span>

<span data-ttu-id="29c58-130">`x:Subclass`可以位於頁面根上或應用程式定義的<xref:System.Windows.Application>根上,該定義已`x:Class`具有 。</span><span class="sxs-lookup"><span data-stu-id="29c58-130">`x:Subclass` can be on a page root or on the <xref:System.Windows.Application> root in the application definition, which already has `x:Class`.</span></span> <span data-ttu-id="29c58-131">在`x:Subclass`頁面或應用程式根以外的任何元素上聲明,或在`x:Class`不存在 時指定它,會導致編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="29c58-131">Declaring `x:Subclass` on any element other than a page or application root, or specifying it where no `x:Class` exists, causes a compile-time error.</span></span>

<span data-ttu-id="29c58-132">創建正確適用於該方案的`x:Subclass`派生類相當複雜。</span><span class="sxs-lookup"><span data-stu-id="29c58-132">Creating derived classes that work correctly for the `x:Subclass` scenario is fairly complex.</span></span> <span data-ttu-id="29c58-133">您可能需要檢查中間檔(通過標記編譯專案 obj 資料夾中生成的 .g 檔,以及包含 .xaml 檔名的名稱)。</span><span class="sxs-lookup"><span data-stu-id="29c58-133">You might need to examine the intermediate files (the .g files produced in the obj folder of your project by markup compile, with names that incorporate the .xaml file names).</span></span> <span data-ttu-id="29c58-134">這些中間檔可以説明您確定編譯應用程式中聯接部分類中某些程式設計構造的來源。</span><span class="sxs-lookup"><span data-stu-id="29c58-134">These intermediate files can help you determine the origin of certain programming constructs in the joined partial classes in the compiled application.</span></span>

<span data-ttu-id="29c58-135">派生類中的事件處理程式必須`internal override``Friend Overrides`( 在 Microsoft Visual Basic 中)才能覆蓋在編譯過程中中間類中創建的處理程式的存根。</span><span class="sxs-lookup"><span data-stu-id="29c58-135">Event handlers in the derived class must be `internal override` (`Friend Overrides` in Microsoft Visual Basic) in order to override the stubs for the handlers as created in the intermediate class during compilation.</span></span> <span data-ttu-id="29c58-136">否則,派生類實現將隱藏(陰影)中間類實現,並且不會調用中間類處理程式。</span><span class="sxs-lookup"><span data-stu-id="29c58-136">Otherwise, the derived class implementations hide (shadow) the intermediate class implementation and the intermediate class handlers are not invoked.</span></span>

<span data-ttu-id="29c58-137">定義`x:Class``x:Subclass`和 時,不需要`x:Class`為引用的類提供任何實現。</span><span class="sxs-lookup"><span data-stu-id="29c58-137">When you define both `x:Class` and `x:Subclass`, you do not need to provide any implementation for the class that is referenced by `x:Class`.</span></span> <span data-ttu-id="29c58-138">您只需透過`x:Class`屬性為其指定名稱,以便編譯器對它在中間檔中創建的類具有一些指導(在這種情況下,編譯器不會選擇預設名稱)。</span><span class="sxs-lookup"><span data-stu-id="29c58-138">You only need to give it a name via the `x:Class` attribute so that the compiler has some guidance for the class that it creates in the intermediate files (the compiler does not select a default name in this case).</span></span> <span data-ttu-id="29c58-139">您可以為`x:Class`類提供一個實現;但是,這不是使用和`x:Class``x:Subclass`的典型方案。</span><span class="sxs-lookup"><span data-stu-id="29c58-139">You can give the `x:Class` class an implementation; however, this is not the typical scenario for using both `x:Class` and `x:Subclass`.</span></span>

## <a name="see-also"></a><span data-ttu-id="29c58-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29c58-140">See also</span></span>

- [<span data-ttu-id="29c58-141">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="29c58-141">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="29c58-142">WPF 的 XAML 和自訂類別</span><span class="sxs-lookup"><span data-stu-id="29c58-142">XAML and Custom Classes for WPF</span></span>](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
