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
ms.openlocfilehash: ea7bc17cba19137b4e4ca2d8cddb32e6630887c9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544839"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="86811-102">x:Code 內建 XAML 類型</span><span class="sxs-lookup"><span data-stu-id="86811-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="86811-103">允許在 XAML 生產環境內放置程式碼。</span><span class="sxs-lookup"><span data-stu-id="86811-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="86811-104">這類程式碼可以由任何編譯 XAML 的 XAML 處理器執行編譯，或留在 XAML 生產環境中，以供稍後使用，例如由執行時間所進行的轉譯。</span><span class="sxs-lookup"><span data-stu-id="86811-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="86811-105">XAML 物件項目用法</span><span class="sxs-lookup"><span data-stu-id="86811-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="86811-106">備註</span><span class="sxs-lookup"><span data-stu-id="86811-106">Remarks</span></span>

<span data-ttu-id="86811-107">Xaml 指示詞元素內的 `x:Code` 程式碼仍會在一般 XML 命名空間和提供的 xaml 命名空間內進行解讀。</span><span class="sxs-lookup"><span data-stu-id="86811-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="86811-108">因此，通常必須將用於區段內的程式碼括住 `x:Code` `CDATA` 。</span><span class="sxs-lookup"><span data-stu-id="86811-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="86811-109">`x:Code` 不允許 XAML 生產環境的所有可能部署機制使用。</span><span class="sxs-lookup"><span data-stu-id="86811-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="86811-110">在特定的 framework (例如 WPF) 必須編譯器代碼。</span><span class="sxs-lookup"><span data-stu-id="86811-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="86811-111">在其他架構中， `x:Code` 通常可能不允許使用。</span><span class="sxs-lookup"><span data-stu-id="86811-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="86811-112">針對允許受控內容的架構 `x:Code` ，用於內容的正確語言編譯器 `x:Code` 是由用來編譯應用程式之包含專案的設定和目標所決定。</span><span class="sxs-lookup"><span data-stu-id="86811-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="86811-113">WPF 使用注意事項</span><span class="sxs-lookup"><span data-stu-id="86811-113">WPF Usage Notes</span></span>

<span data-ttu-id="86811-114">在 `x:Code` FOR WPF 內宣告的程式碼有幾個值得注意的限制：</span><span class="sxs-lookup"><span data-stu-id="86811-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="86811-115">指示詞 `x:Code` 元素必須是 XAML 生產的根項目的直屬子項目。</span><span class="sxs-lookup"><span data-stu-id="86811-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="86811-116">必須在父根項目上提供[x：Class](xclass-directive.md)指示詞。</span><span class="sxs-lookup"><span data-stu-id="86811-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="86811-117">放在裡面的 `x:Code` 程式碼將會被編譯，在部分類別的範圍內，而此部分類別已在該 XAML 頁面中建立。</span><span class="sxs-lookup"><span data-stu-id="86811-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="86811-118">因此，您定義的所有程式碼都必須是該部分類別的成員或變數。</span><span class="sxs-lookup"><span data-stu-id="86811-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="86811-119">除了在部分類別中嵌套類別以外，您也無法定義其他類別 (允許嵌套，但這並不常見，因為無法在 XAML) 中參考嵌套類別。</span><span class="sxs-lookup"><span data-stu-id="86811-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="86811-120">非用於現有部分類別之命名空間的 CLR 命名空間無法定義或新增至。</span><span class="sxs-lookup"><span data-stu-id="86811-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="86811-121">部分類別 CLR 命名空間外部程式碼實體的參考必須全部都是完整的。</span><span class="sxs-lookup"><span data-stu-id="86811-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="86811-122">如果宣告的成員是覆寫部分類別可覆寫成員的，則必須使用特定語言的覆寫關鍵字來指定此成員。</span><span class="sxs-lookup"><span data-stu-id="86811-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="86811-123">如果在範圍中宣告的成員 `x:Code` 與 xaml 所建立之部分類別的成員發生衝突，則在編譯器報告衝突的情況下，XAML 檔案就無法編譯或載入。</span><span class="sxs-lookup"><span data-stu-id="86811-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="86811-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86811-124">See also</span></span>

- [<span data-ttu-id="86811-125">x:Class 指示詞</span><span class="sxs-lookup"><span data-stu-id="86811-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="86811-126">WPF 中的程式碼後置和 XAML</span><span class="sxs-lookup"><span data-stu-id="86811-126">Code-Behind and XAML in WPF</span></span>](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)
- [<span data-ttu-id="86811-127">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="86811-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
