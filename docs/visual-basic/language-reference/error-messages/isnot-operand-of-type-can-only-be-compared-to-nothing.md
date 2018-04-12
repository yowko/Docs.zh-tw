---
title: '&#39; IsNot &#39;運算元的類型 &#39; typename &#39;可以只相較於 &#39;執行任何動作 &#39;，因為 &#39; typename &#39;是可為 null 的型別'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39; IsNot &#39;運算元的類型 &#39; typename &#39;可以只相較於 &#39;執行任何動作 &#39;，因為 &#39; typename &#39;是可為 null 的型別
宣告為可為 null 的變數已被的運算式進行比較以外`Nothing`使用`IsNot`運算子。  
  
 **錯誤 ID:** BC32128  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  要比較的運算式可為 null 的類型以外`Nothing`使用`IsNot`運算子，請呼叫`GetType`方法可為 null 的類型和比較結果與運算式，如下列範例所示。  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>另請參閱  
 [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
