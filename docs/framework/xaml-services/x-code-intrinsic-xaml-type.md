---
title: "x:Code 內建 XAML 類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="d3ffe-102">x:Code 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="d3ffe-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="d3ffe-103">允許在 XAML 生產的程式碼的位置。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="d3ffe-104">這類程式碼可以編譯任何 XAML 處理器實作編譯 XAML 或由執行階段在 XAML 生產的更新版本使用，如解譯左邊。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="d3ffe-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="d3ffe-105">XAML Object Element Usage</span></span>  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="d3ffe-106">備註</span><span class="sxs-lookup"><span data-stu-id="d3ffe-106">Remarks</span></span>  
 <span data-ttu-id="d3ffe-107">中的程式碼`x:Code`XAML 指示詞項目，而且仍然解譯一般的 XML 命名空間中提供的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="d3ffe-108">因此，它是通常會需要使用程式碼括`x:Code`內`CDATA`區段。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="d3ffe-109">`x:Code`不允許用於 XAML 生產的所有可能的部署機制。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="d3ffe-110">必須編譯程式碼中特定架構 (例如 WPF)。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="d3ffe-111">用於其他架構，`x:Code`可能通常不允許使用方式。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="d3ffe-112">允許受管理的介面架構`x:Code`內容，正確的語言編譯器使用`x:Code`內容取決於設定和用來編譯應用程式包含專案的目標。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="d3ffe-113">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="d3ffe-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="d3ffe-114">程式碼中宣告`x:Code`WPF 有一些值得注意的限制：</span><span class="sxs-lookup"><span data-stu-id="d3ffe-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
-   <span data-ttu-id="d3ffe-115">`x:Code`指示詞項目必須是在 XAML 生產的根元素的直系子元素。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
-   <span data-ttu-id="d3ffe-116">[X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)必須提供在父根元素。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-116">[x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) must be provided on the parent root element.</span></span>  
  
-   <span data-ttu-id="d3ffe-117">程式碼置於`x:Code`會編譯到已建立該 XAML 頁面的部分類別的範圍內所處理。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="d3ffe-118">因此您定義的所有程式碼必須是成員或該部分類別的變數。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
-   <span data-ttu-id="d3ffe-119">您不能定義其他類別，而不是藉由巢狀內部的部分類別的類別 （允許巢狀結構，但它不是標準因為無法在 XAML 中參考巢狀的類別）。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="d3ffe-120">無法定義或新增至用於現有的部分類別的命名空間以外的 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
-   <span data-ttu-id="d3ffe-121">部分類別的 CLR 命名空間外部的程式碼實體的參考都必須完全符合規定。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="d3ffe-122">如果宣告的成員會覆寫部分的類別可覆寫的成員，這必須指定以特定語言覆寫的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="d3ffe-123">如果成員宣告中`x:Code`與從 XAML 建立部分類別的成員衝突的範圍、 的方式，編譯器會回報衝突，XAML 檔案無法編譯或載入。</span><span class="sxs-lookup"><span data-stu-id="d3ffe-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ffe-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3ffe-124">See Also</span></span>  
 [<span data-ttu-id="d3ffe-125">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="d3ffe-125">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="d3ffe-126">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="d3ffe-126">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="d3ffe-127">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="d3ffe-127">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
