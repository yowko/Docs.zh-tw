---
title: "'Is' 需要有參考類型的運算元，但此運算元擁有實值類型 '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163346"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="71ca6-102">BC30020： ' Is ' 需要有參考型別的運算元，但此運算元的數值型別為 ' \<typename> '</span><span class="sxs-lookup"><span data-stu-id="71ca6-102">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="71ca6-103">`Is`比較運算子會判斷兩個物件變數是否參考相同的實例。</span><span class="sxs-lookup"><span data-stu-id="71ca6-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="71ca6-104">未針對實數值型別定義這項比較。</span><span class="sxs-lookup"><span data-stu-id="71ca6-104">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="71ca6-105">**錯誤識別碼：** BC30020</span><span class="sxs-lookup"><span data-stu-id="71ca6-105">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="71ca6-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="71ca6-106">To correct this error</span></span>

- <span data-ttu-id="71ca6-107">使用適當的算術比較運算子或 `Like` 運算子來比較兩個實數值型別。</span><span class="sxs-lookup"><span data-stu-id="71ca6-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="71ca6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71ca6-108">See also</span></span>

- [<span data-ttu-id="71ca6-109">Is 運算子</span><span class="sxs-lookup"><span data-stu-id="71ca6-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="71ca6-110">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="71ca6-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="71ca6-111">比較運算子</span><span class="sxs-lookup"><span data-stu-id="71ca6-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
