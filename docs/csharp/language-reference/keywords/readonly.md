---
title: "readonly (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
dev_langs:
- CSharp
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
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
ms.openlocfilehash: 2660aa56721815cbbeb668328863956473cce8f1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="readonly-c-reference"></a><span data-ttu-id="df7a5-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="df7a5-102">readonly (C# Reference)</span></span>
<span data-ttu-id="df7a5-103">`readonly` 關鍵字是您可以在欄位上使用的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="df7a5-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="df7a5-104">欄位宣告包含 `readonly` 修飾詞時，宣告所引進欄位的指派只能出現為宣告的一部分或在相同類別的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="df7a5-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df7a5-105">範例</span><span class="sxs-lookup"><span data-stu-id="df7a5-105">Example</span></span>  
 <span data-ttu-id="df7a5-106">在此範例中，無法變更 `ChangeYear`方法中的 `year` 欄位值，即使它在類別建構函式中獲指派值也是一樣︰</span><span class="sxs-lookup"><span data-stu-id="df7a5-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 <span data-ttu-id="df7a5-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="df7a5-107">[!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]</span></span>  
  
 <span data-ttu-id="df7a5-108">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="df7a5-108">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="df7a5-109">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="df7a5-109">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="df7a5-110">對於執行個體欄位，在包含欄位宣告的類別的執行個體建構函式中，或者，對於靜態欄位，在包含欄位宣告的類別的靜態建構函式中。</span><span class="sxs-lookup"><span data-stu-id="df7a5-110">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="df7a5-111">這些也是適用於將 `readonly` 欄位傳遞為 [out](../../../csharp/language-reference/keywords/out.md) 或 [ref](../../../csharp/language-reference/keywords/ref.md) 參數的唯一內容。</span><span class="sxs-lookup"><span data-stu-id="df7a5-111">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df7a5-112">`readonly` 關鍵字與 [const](../../../csharp/language-reference/keywords/const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="df7a5-112">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="df7a5-113">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="df7a5-113">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="df7a5-114">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="df7a5-114">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="df7a5-115">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="df7a5-115">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="df7a5-116">此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="df7a5-116">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="df7a5-117">範例</span><span class="sxs-lookup"><span data-stu-id="df7a5-117">Example</span></span>  
 <span data-ttu-id="df7a5-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="df7a5-118">[!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]</span></span>  
  
 <span data-ttu-id="df7a5-119">在上述範例中，如果您使用如下的陳述式︰</span><span class="sxs-lookup"><span data-stu-id="df7a5-119">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="df7a5-120">則會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="df7a5-120">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="df7a5-121">這是您嘗試將值指派給常數時所收到的相同錯誤。</span><span class="sxs-lookup"><span data-stu-id="df7a5-121">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="df7a5-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="df7a5-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df7a5-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df7a5-123">See Also</span></span>  
 <span data-ttu-id="df7a5-124">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="df7a5-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="df7a5-125">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="df7a5-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="df7a5-126">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="df7a5-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="df7a5-127">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="df7a5-127">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="df7a5-128">[const](../../../csharp/language-reference/keywords/const.md) </span><span class="sxs-lookup"><span data-stu-id="df7a5-128">[const](../../../csharp/language-reference/keywords/const.md) </span></span>  
 [<span data-ttu-id="df7a5-129">欄位</span><span class="sxs-lookup"><span data-stu-id="df7a5-129">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)

