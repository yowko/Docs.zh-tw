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
# <a name="bc36633-range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>BC36633：範圍變數 \<variable> 隱藏封閉區塊中的變數、先前定義的範圍變數，或查詢運算式中隱含宣告的變數

在、、或子句中指定的範圍變數名稱， `Select` `From` `Aggregate` `Let` 會複製先前在查詢中所指定的範圍變數名稱，或是由查詢隱含宣告的變數名稱，例如功能變數名稱或彙總函式的名稱。

 **錯誤識別碼：** BC36633

## <a name="to-correct-this-error"></a>更正這個錯誤

- 確定特定查詢範圍中的所有範圍變數都有唯一的名稱。 您可以用括弧括住查詢，以確保巢狀查詢具有唯一的範圍。

## <a name="see-also"></a>另請參閱

- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [From 子句](../queries/from-clause.md)
- [Let 子句](../queries/let-clause.md)
- [Aggregate Clause](../queries/aggregate-clause.md)
- [Select 子句](../queries/select-clause.md)
