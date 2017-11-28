---
title: "value (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: value_CSharpKeyword
helpviewer_keywords: value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2501bc8964ed76534dba6c7cc519e095c57cb898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="value-c-reference"></a><span data-ttu-id="0ee6b-102">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0ee6b-102">value (C# Reference)</span></span>
<span data-ttu-id="0ee6b-103">內容關鍵字 `value` 用於一般屬性宣告中的 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="0ee6b-104">類似於方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="0ee6b-105">`value` 一字參考用戶端程式碼嘗試指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="0ee6b-106">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="0ee6b-107">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="0ee6b-108">如需使用 `value` 的詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0ee6b-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0ee6b-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0ee6b-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0ee6b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ee6b-110">See Also</span></span>  
 [<span data-ttu-id="0ee6b-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0ee6b-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0ee6b-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0ee6b-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0ee6b-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0ee6b-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
