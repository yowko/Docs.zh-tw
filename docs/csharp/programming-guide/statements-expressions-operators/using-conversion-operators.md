---
title: 使用轉換運算子 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 17a722f7160ae9cd03caa2dff9c4436fcf0f9d9e
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48845911"
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="d2376-102">使用轉換運算子 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d2376-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="d2376-103">您可以使用比較容易上手的 `implicit` 轉換運算子，或者使用可以向任何人清楚指出您要轉換程式碼的 `explicit` 轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="d2376-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="d2376-104">本主題將示範這兩種類型的轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="d2376-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2376-105">如需簡單類型轉換的資訊，請參閱[如何：將字串轉換為數值](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)、[如何：將位元組陣列轉換成整數](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)、[如何：在十六進位字串和數字類型間轉換](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)或 <xref:System.Convert>。</span><span class="sxs-lookup"><span data-stu-id="d2376-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2376-106">範例</span><span class="sxs-lookup"><span data-stu-id="d2376-106">Example</span></span>  
 <span data-ttu-id="d2376-107">這是明確轉換運算子範例。</span><span class="sxs-lookup"><span data-stu-id="d2376-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="d2376-108">這個運算子會從 <xref:System.Byte> 類型轉換成稱為 `Digit` 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="d2376-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="d2376-109">因為並非所有位元組都可以轉換成數字，所以會明確進行轉換，這表示必須使用轉型，如 `Main` 方法所示。</span><span class="sxs-lookup"><span data-stu-id="d2376-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d2376-110">範例</span><span class="sxs-lookup"><span data-stu-id="d2376-110">Example</span></span>  
 <span data-ttu-id="d2376-111">此範例透過定義可復原上一個範例所執行作業的轉換運算子來示範隱含轉換運算子：它會從稱為 `Digit` 的實值類別轉換成整數 <xref:System.Byte> 類型。</span><span class="sxs-lookup"><span data-stu-id="d2376-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="d2376-112">因為任何數字都可以轉換成 <xref:System.Byte>，所以不需要強制使用者進行明確轉換。</span><span class="sxs-lookup"><span data-stu-id="d2376-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-conversion-operators_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d2376-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="d2376-113">See Also</span></span>

- [<span data-ttu-id="d2376-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d2376-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="d2376-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d2376-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d2376-116">轉換運算子</span><span class="sxs-lookup"><span data-stu-id="d2376-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)  
- [<span data-ttu-id="d2376-117">is</span><span class="sxs-lookup"><span data-stu-id="d2376-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
