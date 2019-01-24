---
title: '&#39;&lt;運算式&gt;&#39;不能當做類型條件約束'
ms.date: 07/20/2015
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords:
- BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
ms.openlocfilehash: b7f77c8113f8af113b4c8515994093958970864a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742129"
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a><span data-ttu-id="b53c9-102">&#39;&lt;運算式&gt;&#39;不能當做類型條件約束</span><span class="sxs-lookup"><span data-stu-id="b53c9-102">&#39;&lt;expression&gt;&#39; cannot be used as a type constraint</span></span>
<span data-ttu-id="b53c9-103">條件約束清單包含運算式，此運算式不表示類型參數上有效的條件約束。</span><span class="sxs-lookup"><span data-stu-id="b53c9-103">A constraint list includes an expression that does not represent a valid constraint on a type parameter.</span></span>  
  
 <span data-ttu-id="b53c9-104">條件約束清單會對傳遞至類型參數的類型引數強制一些必要需求。</span><span class="sxs-lookup"><span data-stu-id="b53c9-104">A constraint list imposes requirements on the type argument passed to the type parameter.</span></span> <span data-ttu-id="b53c9-105">您可以利用任意組合指定下列需求：</span><span class="sxs-lookup"><span data-stu-id="b53c9-105">You can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="b53c9-106">類型引數必須實作一或多個介面</span><span class="sxs-lookup"><span data-stu-id="b53c9-106">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="b53c9-107">類型引數最多只能繼承自一個類別</span><span class="sxs-lookup"><span data-stu-id="b53c9-107">The type argument must inherit from at most one class</span></span>  
  
-   <span data-ttu-id="b53c9-108">類型引數必須公開建立程式碼可以存取的無參數建構函式 (包含 `New` 條件約束)</span><span class="sxs-lookup"><span data-stu-id="b53c9-108">The type argument must expose a parameterless constructor that the creating code can access (include the `New` constraint)</span></span>  
  
 <span data-ttu-id="b53c9-109">如果您未在條件約束清單中包含任何特定類別或介面，則可以指定下列其中一項以強制更一般的需求：</span><span class="sxs-lookup"><span data-stu-id="b53c9-109">If you do not include any specific class or interface in the constraint list, you can impose a more general requirement by specifying one of the following:</span></span>  
  
-   <span data-ttu-id="b53c9-110">類型引數必須是實值類型 (包含 `Structure` 條件約束)</span><span class="sxs-lookup"><span data-stu-id="b53c9-110">The type argument must be a value type (include the `Structure` constraint)</span></span>  
  
-   <span data-ttu-id="b53c9-111">類型引數必須是參考類型 (包含 `Class` 條件約束)</span><span class="sxs-lookup"><span data-stu-id="b53c9-111">The type argument must be a reference type (include the `Class` constraint)</span></span>  
  
 <span data-ttu-id="b53c9-112">您無法針對相同的類型參數同時指定 `Structure` 和 `Class` ，並且無法多次指定其中一個。</span><span class="sxs-lookup"><span data-stu-id="b53c9-112">You cannot specify both `Structure` and `Class` for the same type parameter, and you cannot specify either one more than once.</span></span>  
  
 <span data-ttu-id="b53c9-113">**錯誤 ID:** BC32061</span><span class="sxs-lookup"><span data-stu-id="b53c9-113">**Error ID:** BC32061</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b53c9-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b53c9-114">To correct this error</span></span>  
  
-   <span data-ttu-id="b53c9-115">驗證是否有正確拼寫運算式與它的項目。</span><span class="sxs-lookup"><span data-stu-id="b53c9-115">Verify that the expression and its elements are spelled correctly.</span></span>  
  
-   <span data-ttu-id="b53c9-116">如果運算式不符合上述的需求清單，請將它從條件約束清單中移除。</span><span class="sxs-lookup"><span data-stu-id="b53c9-116">If the expression does not qualify for the preceding list of requirements, remove it from the constraint list.</span></span>  
  
-   <span data-ttu-id="b53c9-117">如果運算式參考介面或類別，請驗證編譯器是否有權存取該介面或類別。</span><span class="sxs-lookup"><span data-stu-id="b53c9-117">If the expression refers to an interface or class, verify that the compiler has access to that interface or class.</span></span> <span data-ttu-id="b53c9-118">您可能需要限定其名稱，而且也可能需要將參考加入專案中。</span><span class="sxs-lookup"><span data-stu-id="b53c9-118">You might need to qualify its name, and you might need to add a reference to your project.</span></span> <span data-ttu-id="b53c9-119">如需詳細資訊，請參閱 < 專案參考 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="b53c9-119">For more information, see "References to Projects" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53c9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b53c9-120">See also</span></span>
- [<span data-ttu-id="b53c9-121">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b53c9-121">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="b53c9-122">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="b53c9-122">Value Types and Reference Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="b53c9-123">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="b53c9-123">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

