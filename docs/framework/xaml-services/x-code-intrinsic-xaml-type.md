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
ms.openlocfilehash: 2b7713548b6269f079ef32b5bf1fe4fa630edcc8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053786"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="f89c3-102">x:Code 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="f89c3-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="f89c3-103">允許在 XAML 生產環境中放置程式碼。</span><span class="sxs-lookup"><span data-stu-id="f89c3-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="f89c3-104">這類程式碼可以由任何編譯 XAML 的 XAML 處理器執行進行編譯，或在 XAML 生產環境中保留，以供稍後使用，例如執行時間的轉譯。</span><span class="sxs-lookup"><span data-stu-id="f89c3-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="f89c3-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="f89c3-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a><span data-ttu-id="f89c3-106">備註</span><span class="sxs-lookup"><span data-stu-id="f89c3-106">Remarks</span></span>  
 <span data-ttu-id="f89c3-107">`x:Code` Xaml 指示詞專案中的程式碼仍會在一般 XML 命名空間和所提供的 XAML 命名空間內加以解讀。</span><span class="sxs-lookup"><span data-stu-id="f89c3-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="f89c3-108">因此，通常需要將用於`x:Code` `CDATA`區段內的程式碼括住。</span><span class="sxs-lookup"><span data-stu-id="f89c3-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>  
  
 <span data-ttu-id="f89c3-109">`x:Code`不允許用於 XAML 生產環境的所有可能部署機制。</span><span class="sxs-lookup"><span data-stu-id="f89c3-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="f89c3-110">在特定架構（例如 WPF）中，必須編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="f89c3-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="f89c3-111">在其他架構中`x:Code` ，通常會不允許使用。</span><span class="sxs-lookup"><span data-stu-id="f89c3-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>  
  
 <span data-ttu-id="f89c3-112">對於允許受控`x:Code`內容的架構，用於`x:Code`內容的正確語言編譯器是由用來編譯應用程式之包含專案的設定和目標所決定。</span><span class="sxs-lookup"><span data-stu-id="f89c3-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="f89c3-113">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="f89c3-113">WPF Usage Notes</span></span>  
 <span data-ttu-id="f89c3-114">在 for WPF `x:Code`中宣告的程式碼有數個值得注意的限制：</span><span class="sxs-lookup"><span data-stu-id="f89c3-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>  
  
- <span data-ttu-id="f89c3-115">`x:Code`指示詞專案必須是 XAML 生產的根項目的直屬子項目。</span><span class="sxs-lookup"><span data-stu-id="f89c3-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>  
  
- <span data-ttu-id="f89c3-116">必須在父根項目上提供[x：Class](x-class-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="f89c3-116">[x:Class Directive](x-class-directive.md) must be provided on the parent root element.</span></span>  
  
- <span data-ttu-id="f89c3-117">放在內`x:Code`的程式碼會由編譯處理，以在已針對該 XAML 頁面建立的部分類別範圍內。</span><span class="sxs-lookup"><span data-stu-id="f89c3-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="f89c3-118">因此，您定義的所有程式碼都必須是該部分類別的成員或變數。</span><span class="sxs-lookup"><span data-stu-id="f89c3-118">Therefore all code you define must be members or variables of that partial class.</span></span>  
  
- <span data-ttu-id="f89c3-119">除了在部分類別中嵌套類別以外，您無法定義其他類別（允許嵌套，但不是一般的，因為在 XAML 中無法參考嵌套類別）。</span><span class="sxs-lookup"><span data-stu-id="f89c3-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="f89c3-120">除了用於現有部分類別的命名空間以外的 CLR 命名空間無法定義或加入至。</span><span class="sxs-lookup"><span data-stu-id="f89c3-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>  
  
- <span data-ttu-id="f89c3-121">部分類別 CLR 命名空間外之程式碼實體的參考必須全部都是完整的。</span><span class="sxs-lookup"><span data-stu-id="f89c3-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="f89c3-122">如果宣告的成員會覆寫至部分類別可重寫成員，則必須使用語言特定的 override 關鍵字來指定。</span><span class="sxs-lookup"><span data-stu-id="f89c3-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="f89c3-123">如果在範圍中`x:Code`宣告的成員與從 XAML 建立之部分類別的成員衝突，則在此情況下，編譯器會報告衝突，XAML 檔案就無法編譯或載入。</span><span class="sxs-lookup"><span data-stu-id="f89c3-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89c3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f89c3-124">See also</span></span>

- [<span data-ttu-id="f89c3-125">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="f89c3-125">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="f89c3-126">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="f89c3-126">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="f89c3-127">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="f89c3-127">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
