---
title: 類型 'typename' 的 'IsNot' 運算元只能與 'Nothing' 比較，因為 'typename' 是可為 Null 的類型
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: caa009606825225dd4063780f9a22fb82f21cf4e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271282"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>類型 'typename' 的 'IsNot' 運算元只能與 'Nothing' 比較，因為 'typename' 是可為 Null 的類型
宣告為可為 null 的變數已經做過比較運算式以外`Nothing`使用`IsNot`運算子。  
  
 **錯誤 ID:** BC32128  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  若要使用 `Nothing` 運算子，將可為 Null 的類型與 `IsNot` 以外的運算式進行比較，請在可為 Null 的類型上呼叫 `GetType` 方法，並將結果與運算式進行比較，如下列範例所示。  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>另請參閱
- [可為 Null 的值類型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
