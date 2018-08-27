---
title: value (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 1e120d68fc4a42f24feb225f652c14525fde3d71
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931938"
---
# <a name="value-c-reference"></a><span data-ttu-id="b689a-102">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b689a-102">value (C# Reference)</span></span>
<span data-ttu-id="b689a-103">內容關鍵字 `value` 用於一般屬性宣告中的 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="b689a-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="b689a-104">類似於方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="b689a-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="b689a-105">`value` 一字參考用戶端程式碼嘗試指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="b689a-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="b689a-106">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="b689a-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="b689a-107">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="b689a-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/value_1.cs)]  
  
 <span data-ttu-id="b689a-108">如需使用 `value` 的詳細資訊，請參閱[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="b689a-108">For more information about the use of `value`, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b689a-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b689a-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b689a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="b689a-110">See Also</span></span>

- [<span data-ttu-id="b689a-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="b689a-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b689a-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b689a-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b689a-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="b689a-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
