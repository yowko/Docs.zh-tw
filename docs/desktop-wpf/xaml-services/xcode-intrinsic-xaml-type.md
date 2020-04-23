---
title: x:Code 內建 XAML 類型
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071553"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="35995-102">x:Code 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="35995-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="35995-103">允許在 XAML 生產中放置代碼。</span><span class="sxs-lookup"><span data-stu-id="35995-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="35995-104">此類代碼可以由編譯 XAML 的任何 XAML 處理器實現編譯,也可以保留在 XAML 生產中供以後使用,例如運行時的解釋。</span><span class="sxs-lookup"><span data-stu-id="35995-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="35995-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="35995-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="35995-106">備註</span><span class="sxs-lookup"><span data-stu-id="35995-106">Remarks</span></span>

<span data-ttu-id="35995-107">`x:Code` XAML 指令元素中的代碼仍在常規 XML 命名空間和提供的 XAML 命名空間中解釋。</span><span class="sxs-lookup"><span data-stu-id="35995-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="35995-108">因此,通常需要將用於段`x:Code`內的代碼封閉`CDATA`。</span><span class="sxs-lookup"><span data-stu-id="35995-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="35995-109">`x:Code`不允許 XAML 生產的所有可能部署機制。</span><span class="sxs-lookup"><span data-stu-id="35995-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="35995-110">在特定框架(例如 WPF)中,必須編譯代碼。</span><span class="sxs-lookup"><span data-stu-id="35995-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="35995-111">在其他框架中,`x:Code`通常可能不允許使用。</span><span class="sxs-lookup"><span data-stu-id="35995-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="35995-112">對於允許託管`x:Code`內容的框架,用於`x:Code`內容的正確語言編譯器由用於編譯應用程式的包含專案的設置和目標確定。</span><span class="sxs-lookup"><span data-stu-id="35995-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="35995-113">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="35995-113">WPF Usage Notes</span></span>

<span data-ttu-id="35995-114">`x:Code`為 WPF 聲明的代碼有幾個值得注意的限制:</span><span class="sxs-lookup"><span data-stu-id="35995-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="35995-115">指令`x:Code`元素必須是 XAML 生產根元素的即時子元素。</span><span class="sxs-lookup"><span data-stu-id="35995-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="35995-116">[x:類指令](xclass-directive.md)必須在父根元素上提供。</span><span class="sxs-lookup"><span data-stu-id="35995-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="35995-117">將位於其中`x:Code`的代碼通過編譯處理為已為該 XAML 頁創建的部分類的範圍。</span><span class="sxs-lookup"><span data-stu-id="35995-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="35995-118">因此,您定義的所有代碼都必須是該部分類的成員或變數。</span><span class="sxs-lookup"><span data-stu-id="35995-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="35995-119">除了在部分類中嵌套類(允許嵌套,但它不是典型的,因為嵌套類無法在 XAML 中引用),因此無法定義其他類。</span><span class="sxs-lookup"><span data-stu-id="35995-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="35995-120">不能定義或添加到現有部分類的命名空間以外的 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="35995-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="35995-121">對部分類 CLR 命名空間外的代碼實體的引用都必須完全限定。</span><span class="sxs-lookup"><span data-stu-id="35995-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="35995-122">如果聲明的成員是覆蓋到部分類重寫成員,則必須使用特定於語言的重寫關鍵字指定此參數。</span><span class="sxs-lookup"><span data-stu-id="35995-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="35995-123">如果在作用網域`x:Code`中 聲明的成員與從 XAML 創建的部分類的成員發生衝突,編譯器報告衝突的方式,XAML 檔無法編譯或載入。</span><span class="sxs-lookup"><span data-stu-id="35995-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="35995-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35995-124">See also</span></span>

- [<span data-ttu-id="35995-125">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="35995-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="35995-126">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="35995-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="35995-127">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="35995-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
