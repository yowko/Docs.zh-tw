---
title: public (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960240"
---
# <a name="public-c-reference"></a><span data-ttu-id="bb6e0-102">public (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bb6e0-102">public (C# Reference)</span></span>
<span data-ttu-id="bb6e0-103">`public` 關鍵字是類型和類型成員的存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="bb6e0-104">公用存取是最寬鬆的存取層級。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="bb6e0-105">不會限制存取公用成員，如此範例所示︰</span><span class="sxs-lookup"><span data-stu-id="bb6e0-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="bb6e0-106">如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)和[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb6e0-107">範例</span><span class="sxs-lookup"><span data-stu-id="bb6e0-107">Example</span></span>  
 <span data-ttu-id="bb6e0-108">在下列範例中，宣告兩個類別：`PointTest` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="bb6e0-109">`PointTest`的公用成員 `x` 和 `y` 直接存取自 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="bb6e0-110">如果您將 `public` 存取層級變更為 [private](../../../csharp/language-reference/keywords/private.md) 或 [protected](../../../csharp/language-reference/keywords/protected.md)，則會收到錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="bb6e0-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="bb6e0-111">'PointTest.y' 的保護層級導致無法對其進行存取。</span><span class="sxs-lookup"><span data-stu-id="bb6e0-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bb6e0-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bb6e0-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb6e0-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb6e0-113">See Also</span></span>  
 [<span data-ttu-id="bb6e0-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bb6e0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bb6e0-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bb6e0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bb6e0-116">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="bb6e0-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="bb6e0-117">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bb6e0-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bb6e0-118">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="bb6e0-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="bb6e0-119">存取範圍層級</span><span class="sxs-lookup"><span data-stu-id="bb6e0-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="bb6e0-120">修飾詞</span><span class="sxs-lookup"><span data-stu-id="bb6e0-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="bb6e0-121">private</span><span class="sxs-lookup"><span data-stu-id="bb6e0-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="bb6e0-122">protected</span><span class="sxs-lookup"><span data-stu-id="bb6e0-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="bb6e0-123">internal</span><span class="sxs-lookup"><span data-stu-id="bb6e0-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
