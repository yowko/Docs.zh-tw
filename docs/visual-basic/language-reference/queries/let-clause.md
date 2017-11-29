---
title: "Let 子句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a>Let 子句 (Visual Basic)
計算值，並將它指派給查詢中的新變數。  
  
## <a name="syntax"></a>語法  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`variable`|必要項。 別名可以用來參考提供運算式的結果。|  
|`expression`|必要項。 運算式，會進行評估，並指派給指定的變數。|  
  
## <a name="remarks"></a>備註  
 `Let`子句可讓您用來計算每個值查詢結果，並使用別名來參考它們。 別名可用於其他子句，例如`Where`子句。 `Let`子句可讓您建立更容易讀取，因為您可以指定包含在查詢運算式子句的別名，並以別名取代每次使用時的運算式子句的查詢陳述式。  
  
 您可以包含任意數目的`variable`和`expression`中的指派`Let`子句。 請以逗號 （，） 分隔每個指派。  
  
## <a name="example"></a>範例  
 下列程式碼範例使用`Let`子句來計算產品的 10%折扣。  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [查詢](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 子句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 子句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Where 子句](../../../visual-basic/language-reference/queries/where-clause.md)
