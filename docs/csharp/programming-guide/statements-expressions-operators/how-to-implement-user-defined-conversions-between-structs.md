---
title: 作法：在結構之間實作使用者定義的轉換 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- user-defined conversions [C#]
ms.assetid: 97839aef-8fbc-40d5-9769-6b569bc2710b
ms.openlocfilehash: f33d8791791543704c8a49a44167b94c0f0c86b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608165"
---
# <a name="how-to-implement-user-defined-conversions-between-structs-c-programming-guide"></a><span data-ttu-id="c16ef-102">作法：在結構之間實作使用者定義的轉換 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="c16ef-102">How to: Implement User-Defined Conversions Between Structs (C# Programming Guide)</span></span>
<span data-ttu-id="c16ef-103">這個範例會定義兩個結構 `RomanNumeral` 和 `BinaryNumeral`，並示範它們的轉換。</span><span class="sxs-lookup"><span data-stu-id="c16ef-103">This example defines two structs, `RomanNumeral` and `BinaryNumeral`, and demonstrates conversions between them.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c16ef-104">範例</span><span class="sxs-lookup"><span data-stu-id="c16ef-104">Example</span></span>  
 [!code-csharp[csProgGuideStatements#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c16ef-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c16ef-105">Robust Programming</span></span>  
  
- <span data-ttu-id="c16ef-106">上例中，陳述式：</span><span class="sxs-lookup"><span data-stu-id="c16ef-106">In the previous example, the statement:</span></span>  
  
     [!code-csharp[csProgGuideStatements#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#14)]  
  
     <span data-ttu-id="c16ef-107">執行從 `RomanNumeral` 到 `BinaryNumeral` 的轉換。</span><span class="sxs-lookup"><span data-stu-id="c16ef-107">performs a conversion from a `RomanNumeral` to a `BinaryNumeral`.</span></span> <span data-ttu-id="c16ef-108">因為沒有直接從 `RomanNumeral` 轉換至 `BinaryNumeral`，所以使用 cast 從 `RomanNumeral` 轉換成 `int`，再使用另一個 cast 從 `int` 轉換成 `BinaryNumeral`。</span><span class="sxs-lookup"><span data-stu-id="c16ef-108">Because there is no direct conversion from `RomanNumeral` to `BinaryNumeral`, a cast is used to convert from a `RomanNumeral` to an `int`, and another cast to convert from an `int` to a `BinaryNumeral`.</span></span>  
  
- <span data-ttu-id="c16ef-109">也是陳述式</span><span class="sxs-lookup"><span data-stu-id="c16ef-109">Also the statement</span></span>  
  
     [!code-csharp[csProgGuideStatements#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#15)]  
  
     <span data-ttu-id="c16ef-110">執行從 `BinaryNumeral` 到 `RomanNumeral` 的轉換。</span><span class="sxs-lookup"><span data-stu-id="c16ef-110">performs a conversion from a `BinaryNumeral` to a `RomanNumeral`.</span></span> <span data-ttu-id="c16ef-111">因為 `RomanNumeral` 定義 `BinaryNumeral` 的隱含轉換，所以不需要任何轉換。</span><span class="sxs-lookup"><span data-stu-id="c16ef-111">Because `RomanNumeral` defines an implicit conversion from `BinaryNumeral`, no cast is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16ef-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c16ef-112">See also</span></span>

- [<span data-ttu-id="c16ef-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c16ef-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c16ef-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c16ef-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c16ef-115">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="c16ef-115">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
