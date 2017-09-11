---
title: "const (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
dev_langs:
- CSharp
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b8f6d567deed513ff5693fe39bd21c8607677402
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="const-c-reference"></a><span data-ttu-id="1aa09-102">const (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1aa09-102">const (C# Reference)</span></span>
<span data-ttu-id="1aa09-103">您可以使用 `const` 關鍵字來宣告常數欄位或區域常數。</span><span class="sxs-lookup"><span data-stu-id="1aa09-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="1aa09-104">常數欄位和區域常數不是變數，可能無法修改。</span><span class="sxs-lookup"><span data-stu-id="1aa09-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="1aa09-105">常數可以是數值、布林值、字串或 null 參考。</span><span class="sxs-lookup"><span data-stu-id="1aa09-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="1aa09-106">請勿建立用來表示想隨時變更之資訊的常數。</span><span class="sxs-lookup"><span data-stu-id="1aa09-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="1aa09-107">例如，請勿使用常數欄位來儲存服務的價格、產品版本號碼或公司的品牌名稱。</span><span class="sxs-lookup"><span data-stu-id="1aa09-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="1aa09-108">這些值可能會隨時間變更；此外，由於編譯器會傳播常數，以您的程式庫編譯的其他程式碼必須經過重新編譯，才能看到變更。</span><span class="sxs-lookup"><span data-stu-id="1aa09-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="1aa09-109">另請參閱 [readonly](../../../csharp/language-reference/keywords/readonly.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="1aa09-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="1aa09-110">例如: </span><span class="sxs-lookup"><span data-stu-id="1aa09-110">For example:</span></span>  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a><span data-ttu-id="1aa09-111">備註</span><span class="sxs-lookup"><span data-stu-id="1aa09-111">Remarks</span></span>  
 <span data-ttu-id="1aa09-112">常數宣告的類型指定宣告引入的成員類型。</span><span class="sxs-lookup"><span data-stu-id="1aa09-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="1aa09-113">區域常數或常數欄位的初始設定式必須是可明確轉換成目標類型的常數運算式。</span><span class="sxs-lookup"><span data-stu-id="1aa09-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>  
  
 <span data-ttu-id="1aa09-114">常數運算式是可在編譯時期完整評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="1aa09-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="1aa09-115">因此，參考類型之常數唯一可能的值為 `string` 和 null 參考。</span><span class="sxs-lookup"><span data-stu-id="1aa09-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>  
  
 <span data-ttu-id="1aa09-116">常數宣告可以宣告多個常數，例如：</span><span class="sxs-lookup"><span data-stu-id="1aa09-116">The constant declaration can declare multiple constants, such as:</span></span>  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 <span data-ttu-id="1aa09-117">常數宣告中不允許使用 `static` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="1aa09-117">The `static` modifier is not allowed in a constant declaration.</span></span>  
  
 <span data-ttu-id="1aa09-118">常數可以參與常數運算式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1aa09-118">A constant can participate in a constant expression, as follows:</span></span>  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  <span data-ttu-id="1aa09-119">[readonly](../../../csharp/language-reference/keywords/readonly.md) 關鍵字與 `const` 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="1aa09-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="1aa09-120">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="1aa09-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="1aa09-121">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="1aa09-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="1aa09-122">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="1aa09-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="1aa09-123">此外，雖然 `const` 欄位是編譯時期常數，但 `readonly` 欄位可用於執行階段常數，如下列程式碼所示：`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="1aa09-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa09-124">範例</span><span class="sxs-lookup"><span data-stu-id="1aa09-124">Example</span></span>  
 <span data-ttu-id="1aa09-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1aa09-125">[!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aa09-126">範例</span><span class="sxs-lookup"><span data-stu-id="1aa09-126">Example</span></span>  
 <span data-ttu-id="1aa09-127">這個範例示範如何將常數當做區域變數來使用。</span><span class="sxs-lookup"><span data-stu-id="1aa09-127">This example demonstrates how to use constants as local variables.</span></span>  
  
 <span data-ttu-id="1aa09-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1aa09-128">[!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1aa09-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1aa09-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1aa09-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aa09-130">See Also</span></span>  
 <span data-ttu-id="1aa09-131">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1aa09-131">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1aa09-132">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1aa09-132">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1aa09-133">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="1aa09-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="1aa09-134">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="1aa09-134">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="1aa09-135">readonly</span><span class="sxs-lookup"><span data-stu-id="1aa09-135">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)

