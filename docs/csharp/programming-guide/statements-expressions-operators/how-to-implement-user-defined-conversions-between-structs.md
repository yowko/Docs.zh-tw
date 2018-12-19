---
title: HOW TO：在結構之間實作使用者定義的轉換 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: 85345203982679c0ab8dc9a6ae899312204c3230
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241570"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="13568-102">HOW TO：在結構之間實作使用者定義的轉換 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="13568-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="13568-103">這個範例會定義兩個結構 `RomanNumeral` 和 `BinaryNumeral`，並示範它們的轉換。</span><span class="sxs-lookup"><span data-stu-id="13568-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13568-104">範例</span><span class="sxs-lookup"><span data-stu-id="13568-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="13568-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="13568-105">Robust Programming</span></span>  
  
-   <span data-ttu-id="13568-106">上例中，陳述式：</span><span class="sxs-lookup"><span data-stu-id="13568-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_2.cs)]  
  
     <span data-ttu-id="13568-107">執行從 `RomanNumeral` 到 `BinaryNumeral` 的轉換。</span><span class="sxs-lookup"><span data-stu-id="13568-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="13568-108">因為沒有直接從 `RomanNumeral` 轉換至 `BinaryNumeral`，所以使用 cast 從 `RomanNumeral` 轉換成 `int`，再使用另一個 cast 從 `int` 轉換成 `BinaryNumeral`。</span><span class="sxs-lookup"><span data-stu-id="13568-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
-   <span data-ttu-id="13568-109">也是陳述式</span><span class="sxs-lookup"><span data-stu-id="13568-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-user-defined-conversions-between-structs_3.cs)]  
  
     <span data-ttu-id="13568-110">執行從 `BinaryNumeral` 到 `RomanNumeral` 的轉換。</span><span class="sxs-lookup"><span data-stu-id="13568-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="13568-111">因為 `RomanNumeral` 定義 `BinaryNumeral` 的隱含轉換，所以不需要任何轉換。</span><span class="sxs-lookup"><span data-stu-id="13568-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13568-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="13568-112">See Also</span></span>

- [<span data-ttu-id="13568-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="13568-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="13568-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="13568-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="13568-115">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="13568-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
