---
title: readonly (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d2f8a2f192dc319ad806aeef4bfbaeecc44b07a3
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="readonly-c-reference"></a><span data-ttu-id="a11ec-102">readonly (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a11ec-102">readonly (C# Reference)</span></span>
<span data-ttu-id="a11ec-103">`readonly` 關鍵字是您可以在欄位上使用的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="a11ec-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="a11ec-104">欄位宣告包含 `readonly` 修飾詞時，宣告所引進欄位的指派只能出現為宣告的一部分或在相同類別的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="a11ec-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="readonly-field-example"></a><span data-ttu-id="a11ec-105">唯讀欄位範例</span><span class="sxs-lookup"><span data-stu-id="a11ec-105">Readonly field example</span></span>  
 <span data-ttu-id="a11ec-106">在此範例中，無法變更 `ChangeYear`方法中的 `year` 欄位值，即使它在類別建構函式中獲指派值也是一樣︰</span><span class="sxs-lookup"><span data-stu-id="a11ec-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="a11ec-107">您只能在下列內容中將值指派給 `readonly` 欄位︰</span><span class="sxs-lookup"><span data-stu-id="a11ec-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="a11ec-108">在宣告中初始化變數時，例如︰</span><span class="sxs-lookup"><span data-stu-id="a11ec-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```csharp  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="a11ec-109">對於執行個體欄位，在包含欄位宣告的類別的執行個體建構函式中，或者，對於靜態欄位，在包含欄位宣告的類別的靜態建構函式中。</span><span class="sxs-lookup"><span data-stu-id="a11ec-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="a11ec-110">這些也是適用於將 `readonly` 欄位傳遞為 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 或 [ref](../../../csharp/language-reference/keywords/ref.md) 參數的唯一內容。</span><span class="sxs-lookup"><span data-stu-id="a11ec-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a11ec-111">`readonly` 關鍵字與 [const](../../../csharp/language-reference/keywords/const.md) 關鍵字不同。</span><span class="sxs-lookup"><span data-stu-id="a11ec-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="a11ec-112">`const` 欄位只能在欄位的宣告中初始化。</span><span class="sxs-lookup"><span data-stu-id="a11ec-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="a11ec-113">`readonly` 欄位可在宣告或建構函式中初始化。</span><span class="sxs-lookup"><span data-stu-id="a11ec-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="a11ec-114">因此，`readonly` 欄位可能會因使用的建構函式而有不同的值。</span><span class="sxs-lookup"><span data-stu-id="a11ec-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="a11ec-115">此外，雖然 `const` 欄位是編譯時間常數，但是 `readonly` 欄位可用於執行階段常數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a11ec-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```csharp  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a><span data-ttu-id="a11ec-116">比較唯讀及非唯讀執行個體欄位</span><span class="sxs-lookup"><span data-stu-id="a11ec-116">Comparing readonly and non-readonly instance fields</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="a11ec-117">在上述範例中，如果您使用如下的陳述式︰</span><span class="sxs-lookup"><span data-stu-id="a11ec-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="a11ec-118">則會收到編譯器錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="a11ec-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="a11ec-119">這是您嘗試將值指派給常數時所收到的相同錯誤。</span><span class="sxs-lookup"><span data-stu-id="a11ec-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a11ec-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="a11ec-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a11ec-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a11ec-121">See Also</span></span>  
 [<span data-ttu-id="a11ec-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a11ec-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a11ec-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a11ec-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a11ec-124">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a11ec-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a11ec-125">修飾詞</span><span class="sxs-lookup"><span data-stu-id="a11ec-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="a11ec-126">const</span><span class="sxs-lookup"><span data-stu-id="a11ec-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="a11ec-127">欄位</span><span class="sxs-lookup"><span data-stu-id="a11ec-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
