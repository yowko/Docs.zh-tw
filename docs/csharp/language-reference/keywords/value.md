---
title: "value (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- value_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: 14
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
ms.openlocfilehash: 012cf622091687996fec477a8b5b821b190bbc29
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="value-c-reference"></a><span data-ttu-id="bddad-102">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bddad-102">value (C# Reference)</span></span>
<span data-ttu-id="bddad-103">內容關鍵字 `value` 用於一般屬性宣告中的 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="bddad-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="bddad-104">類似於方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="bddad-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="bddad-105">`value` 一字參考用戶端程式碼嘗試指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bddad-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="bddad-106">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="bddad-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="bddad-107">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="bddad-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 <span data-ttu-id="bddad-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="bddad-108">[!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]</span></span>  
  
 <span data-ttu-id="bddad-109">如需使用 `value` 的詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bddad-109">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bddad-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bddad-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bddad-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bddad-111">See Also</span></span>  
 <span data-ttu-id="bddad-112">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bddad-112">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bddad-113">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bddad-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="bddad-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bddad-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

