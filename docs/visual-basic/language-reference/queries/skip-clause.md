---
title: "Skip 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a>Skip 子句 (Visual Basic)
略過集合中指定數目的項目，然後傳回其餘項目。  
  
## <a name="syntax"></a>語法  
  
```  
Skip count  
```  
  
## <a name="parts"></a>組件  
 `count`  
 必要項。 值或運算式評估為略過序列的項目數目。  
  
## <a name="remarks"></a>備註  
 `Skip`子句會讓查詢略過的結果清單開頭的項目，然後傳回其餘項目。 略過的項目數由`count`參數。  
  
 您可以使用`Skip`子句搭配`Take`子句傳回的資料範圍查詢的任何區段。 若要這樣做，傳遞到範圍內的第一個元素索引`Skip`子句和範圍的大小`Take`子句。  
  
 當您使用`Skip`子句的查詢中，您可能也需要確保結果會傳回順序將會啟用`Skip`子句來略過所要的結果。 如需排序查詢結果的詳細資訊，請參閱[Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)。  
  
 您可以使用`SkipWhile`子句來指定，忽略特定項目，根據提供的條件。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Skip`子句搭配`Take`子句，從頁面中的查詢傳回資料。 `GetCustomers`函式使用`Skip`子句來略過清單中的客戶，直到提供開始索引值，並使用`Take`子句傳回的客戶，從該索引值開始的頁面。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By 子句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take 子句](../../../visual-basic/language-reference/queries/take-clause.md)
