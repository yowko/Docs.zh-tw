---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 42bde0b1843e52bbc16118bb056ade791591904e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249496"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>在此內容中不支援可為 Null 的類型推斷
數值型別和結構可以聲明為空。  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 但是，不能將可無效聲明與型別推斷結合使用。 以下示例導致此錯誤。  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **錯誤 ID：** BC36629  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用`As`子句將變數聲明為空數值型別。  
  
## <a name="see-also"></a>另請參閱

- [空數值型別](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [區域型別推斷](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
