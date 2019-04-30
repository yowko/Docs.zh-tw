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
ms.openlocfilehash: 7bb78b05be7b3edc4471bc276010eabd92a07a14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971843"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="55c77-102">x:Code 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="55c77-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="55c77-103">可讓 XAML 生產環境中的程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="55c77-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="55c77-104">可以將 XAML 或留在稍後使用，例如解譯的 XAML 生產環境中的執行階段編譯任何 XAML 處理器實作編譯這類程式碼。</span><span class="sxs-lookup"><span data-stu-id="55c77-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="55c77-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="55c77-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="55c77-106">備註</span><span class="sxs-lookup"><span data-stu-id="55c77-106">Remarks</span></span>  
 <span data-ttu-id="55c77-107">中的程式碼`x:Code`XAML 指示詞項目是仍在一般的 XML 命名空間中解譯和提供的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="55c77-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="55c77-108">因此，它是括住的程式碼通常會需要`x:Code`內`CDATA`區段。</span><span class="sxs-lookup"><span data-stu-id="55c77-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="55c77-109">`x:Code` 不允許針對 XAML 生產的所有可能的部署機制。</span><span class="sxs-lookup"><span data-stu-id="55c77-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="55c77-110">在特定架構 (例如 WPF) 中程式碼必須編譯。</span><span class="sxs-lookup"><span data-stu-id="55c77-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="55c77-111">在 其他架構，`x:Code`可能通常不允許使用方式。</span><span class="sxs-lookup"><span data-stu-id="55c77-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="55c77-112">允許受管理的架構`x:Code`內容，正確的語言編譯器使用`x:Code`內容取決於設定和用來編譯應用程式所包含專案的目標。</span><span class="sxs-lookup"><span data-stu-id="55c77-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="55c77-113">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="55c77-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="55c77-114">程式碼內宣告`x:Code`WPF 有幾個值得注意的限制：</span><span class="sxs-lookup"><span data-stu-id="55c77-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="55c77-115">`x:Code`指示詞項目必須是 XAML 生產的根元素的直系子元素。</span><span class="sxs-lookup"><span data-stu-id="55c77-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="55c77-116">[X:class 指示詞](x-class-directive.md)必須提供在父根項目。</span><span class="sxs-lookup"><span data-stu-id="55c77-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="55c77-117">程式碼置於`x:Code`會被編譯到已建立該 XAML 頁面的部分類別的範圍內。</span><span class="sxs-lookup"><span data-stu-id="55c77-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="55c77-118">因此您所定義的所有程式碼必須是成員或該部分類別的變數。</span><span class="sxs-lookup"><span data-stu-id="55c77-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="55c77-119">您不能定義其他類別，而非巢狀內的部分類別的類別 （允許巢狀結構，但它不是一般因為 XAML 中不得參考巢狀的類別）。</span><span class="sxs-lookup"><span data-stu-id="55c77-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="55c77-120">無法定義或加入至用於現有的部分類別的命名空間以外的 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="55c77-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="55c77-121">部分類別的 CLR 命名空間外部的程式碼實體的參考必須全部是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="55c77-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="55c77-122">如果宣告的成員會覆寫部分類別可覆寫成員，這必須指定與語言特定覆寫的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="55c77-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="55c77-123">如果成員宣告中`x:Code`與 XAML 建立的部分類別的成員相衝突的範圍，一種，編譯器會報告衝突，XAML 檔案無法編譯或載入。</span><span class="sxs-lookup"><span data-stu-id="55c77-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c77-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55c77-124">See also</span></span>

- [<span data-ttu-id="55c77-125">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="55c77-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="55c77-126">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="55c77-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="55c77-127">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="55c77-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
