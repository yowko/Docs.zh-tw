---
title: 存取範圍定義域 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713828"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="beef4-102">存取範圍定義域 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="beef4-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="beef4-103">成員的存取範圍定義域指定可參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="beef4-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="beef4-104">如果成員巢狀在另一個類型內，則其存取範圍定義域是由成員的[存取範圍層級](./accessibility-levels.md)和立即包含類型的存取範圍定義域所決定。</span><span class="sxs-lookup"><span data-stu-id="beef4-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="beef4-105">最上層類型的存取範圍定義域是至少在其中宣告之專案的程式文字。</span><span class="sxs-lookup"><span data-stu-id="beef4-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="beef4-106">亦即，定義域包括此專案的所有原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="beef4-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="beef4-107">巢狀型別的存取範圍定義域是至少在其中宣告之類型的程式文字。</span><span class="sxs-lookup"><span data-stu-id="beef4-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="beef4-108">亦即，定義域是包括所有巢狀型別的類型主體。</span><span class="sxs-lookup"><span data-stu-id="beef4-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="beef4-109">巢狀型別的存取範圍定義域絕不會超過包含類型的存取範圍定義域。</span><span class="sxs-lookup"><span data-stu-id="beef4-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="beef4-110">下列範例示範這些概念。</span><span class="sxs-lookup"><span data-stu-id="beef4-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beef4-111">範例</span><span class="sxs-lookup"><span data-stu-id="beef4-111">Example</span></span>  
 <span data-ttu-id="beef4-112">這個範例包含最上層類型 `T1` 以及兩個巢狀類別 `M1` 和 `M2`。</span><span class="sxs-lookup"><span data-stu-id="beef4-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="beef4-113">這些類別包含具有不同已宣告存取範圍的欄位。</span><span class="sxs-lookup"><span data-stu-id="beef4-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="beef4-114">在 `Main` 方法中，註解在每個陳述式的後面，表示每個成員的存取領域。</span><span class="sxs-lookup"><span data-stu-id="beef4-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="beef4-115">請注意，嘗試引用無法訪問的成員的語句將注釋掉。如果要查看引用不可訪問的成員而導致的編譯器錯誤，請一次刪除一個注釋。</span><span class="sxs-lookup"><span data-stu-id="beef4-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="beef4-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="beef4-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="beef4-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beef4-117">See also</span></span>

- [<span data-ttu-id="beef4-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="beef4-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="beef4-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="beef4-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="beef4-120">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="beef4-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="beef4-121">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="beef4-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="beef4-122">協助工具級別</span><span class="sxs-lookup"><span data-stu-id="beef4-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="beef4-123">使用協助工具級別的限制</span><span class="sxs-lookup"><span data-stu-id="beef4-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="beef4-124">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="beef4-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="beef4-125">public</span><span class="sxs-lookup"><span data-stu-id="beef4-125">public</span></span>](./public.md)
- [<span data-ttu-id="beef4-126">私人</span><span class="sxs-lookup"><span data-stu-id="beef4-126">private</span></span>](./private.md)
- [<span data-ttu-id="beef4-127">保護</span><span class="sxs-lookup"><span data-stu-id="beef4-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="beef4-128">內部</span><span class="sxs-lookup"><span data-stu-id="beef4-128">internal</span></span>](./internal.md)
