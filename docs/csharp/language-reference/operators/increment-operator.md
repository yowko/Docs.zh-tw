---
title: ++ 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45593097"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="58d93-102">++ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="58d93-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="58d93-103">遞增運算子 (`++`) 的運算元遞增量為 1。</span><span class="sxs-lookup"><span data-stu-id="58d93-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="58d93-104">遞增運算子可以出現在其運算元的前後： `++variable` 和 `variable++`。</span><span class="sxs-lookup"><span data-stu-id="58d93-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58d93-105">備註</span><span class="sxs-lookup"><span data-stu-id="58d93-105">Remarks</span></span>  
 <span data-ttu-id="58d93-106">第一種形式是前置詞遞增作業。</span><span class="sxs-lookup"><span data-stu-id="58d93-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="58d93-107">作業的結果是運算元已遞增之後的值。</span><span class="sxs-lookup"><span data-stu-id="58d93-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="58d93-108">第二種形式是後置遞增作業。</span><span class="sxs-lookup"><span data-stu-id="58d93-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="58d93-109">作業的結果是運算元遞增之前的值。</span><span class="sxs-lookup"><span data-stu-id="58d93-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="58d93-110">數字和列舉型別有預先定義的遞增運算子。</span><span class="sxs-lookup"><span data-stu-id="58d93-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="58d93-111">使用者定義類型可以多載 `++` 運算子。</span><span class="sxs-lookup"><span data-stu-id="58d93-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="58d93-112">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="58d93-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58d93-113">範例</span><span class="sxs-lookup"><span data-stu-id="58d93-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="58d93-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="58d93-114">See Also</span></span>

- [<span data-ttu-id="58d93-115">C# 參考</span><span class="sxs-lookup"><span data-stu-id="58d93-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="58d93-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="58d93-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="58d93-117">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="58d93-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
