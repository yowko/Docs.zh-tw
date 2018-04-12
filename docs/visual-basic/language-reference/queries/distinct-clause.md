---
title: Distinct 子句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a>Distinct 子句 (Visual Basic)
限制目前的範圍變數，以消除重複的值，在後續的查詢子句中的值。  
  
## <a name="syntax"></a>語法  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>備註  
 您可以使用`Distinct`子句，傳回唯一項目清單。 `Distinct`子句會讓查詢略過重複的查詢結果。 `Distinct`子句套用到重複的值，所有傳回指定的欄位`Select`子句。 如果沒有`Select`指定子句，`Distinct`子句會套用到查詢中所識別的範圍變數`From`子句。 如果範圍變數不是不可變的類型，查詢將只略過查詢結果型別的所有成員符合現有查詢的結果。  
  
## <a name="example"></a>範例  
 下列查詢運算式會聯結一份客戶與客戶訂單的清單。 `Distinct`子句也會傳回一份唯一客戶名稱及訂購日期。  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
