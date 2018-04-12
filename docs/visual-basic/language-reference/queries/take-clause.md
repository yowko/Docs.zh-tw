---
title: Take 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a>Take 子句 (Visual Basic)
從集合開頭傳回指定數目的連續項目。  
  
## <a name="syntax"></a>語法  
  
```  
Take count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要項。 值或評估運算式傳回序列的項目數目。  
  
## <a name="remarks"></a>備註  
 `Take`子句，會使查詢包含連續的項目，從結果清單的開頭指定的數目。 所指定要包含的項目數`count`參數。  
  
 您可以使用`Take`子句搭配`Skip`子句傳回的資料範圍查詢的任何區段。 若要這樣做，傳遞到範圍內的第一個元素索引`Skip`子句和範圍的大小`Take`子句。 在此情況下，`Take`子句必須指定後面`Skip`子句。  
  
 當您使用`Take`子句的查詢中，您可能也需要確保結果會傳回順序將會啟用`Take`子句，以包含所要的結果。 如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用`TakeWhile`子句來指定傳回特定項目，根據提供的條件。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Take`子句搭配`Skip`子句，從頁面中的查詢傳回資料。 GetCustomers 函式使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip 子句](../../../visual-basic/language-reference/queries/skip-clause.md)
