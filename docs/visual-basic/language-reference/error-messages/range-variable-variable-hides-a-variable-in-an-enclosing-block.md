---
title: 範圍變數 <variable> 隱藏了封閉區塊中的變數、預先定義的範圍變數或查詢運算式中隱含宣告的變數
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 90fed3dd27f18fe87c326cc36dfb774822fc4b21
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162345"
---
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="28001-102">BC36633：範圍變數 \<variable> 隱藏封閉區塊中的變數、先前定義的範圍變數，或查詢運算式中隱含宣告的變數</span><span class="sxs-lookup"><span data-stu-id="28001-102">BC36633: Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>

<span data-ttu-id="28001-103">在、、或子句中指定的範圍變數名稱， `Select` `From` `Aggregate` `Let` 會複製先前在查詢中所指定的範圍變數名稱，或是由查詢隱含宣告的變數名稱，例如功能變數名稱或彙總函式的名稱。</span><span class="sxs-lookup"><span data-stu-id="28001-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>

 <span data-ttu-id="28001-104">**錯誤識別碼：** BC36633</span><span class="sxs-lookup"><span data-stu-id="28001-104">**Error ID:** BC36633</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="28001-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="28001-105">To correct this error</span></span>

- <span data-ttu-id="28001-106">確定特定查詢範圍中的所有範圍變數都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="28001-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="28001-107">您可以用括弧括住查詢，以確保巢狀查詢具有唯一的範圍。</span><span class="sxs-lookup"><span data-stu-id="28001-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>

## <a name="see-also"></a><span data-ttu-id="28001-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28001-108">See also</span></span>

- [<span data-ttu-id="28001-109">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="28001-109">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="28001-110">From 子句</span><span class="sxs-lookup"><span data-stu-id="28001-110">From Clause</span></span>](../queries/from-clause.md)
- [<span data-ttu-id="28001-111">Let 子句</span><span class="sxs-lookup"><span data-stu-id="28001-111">Let Clause</span></span>](../queries/let-clause.md)
- [<span data-ttu-id="28001-112">Aggregate Clause</span><span class="sxs-lookup"><span data-stu-id="28001-112">Aggregate Clause</span></span>](../queries/aggregate-clause.md)
- [<span data-ttu-id="28001-113">Select 子句</span><span class="sxs-lookup"><span data-stu-id="28001-113">Select Clause</span></span>](../queries/select-clause.md)
