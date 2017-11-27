---
title: "在此內容中不支援可為 Null 的類型推斷"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords: BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e7a5450d812260d3916296dff56abee27b3d586c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>在此內容中不支援可為 Null 的類型推斷
實值類型和結構可以宣告為可為 null。  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 不過，您無法使用可為 null 的宣告型別推斷結合。 下列範例會造成這個錯誤。  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **錯誤 ID:** BC36629  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用`As`子句來宣告為可為 null 的變數。  
  
## <a name="see-also"></a>另請參閱  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [區域類型推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
