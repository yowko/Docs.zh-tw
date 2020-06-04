---
title: 在此內容中不支援可為 Null 的類型推斷
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 52e5391fbcf30a4dada4d64a0e810c900ea85806
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409383"
---
# <a name="nullable-type-inference-is-not-supported-in-this-context"></a>在此內容中不支援可為 Null 的類型推斷
實數值型別和結構可以宣告為可為 null。  
  
```vb  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 不過，您不能將可為 null 的宣告與型別推斷搭配使用。 下列範例會造成此錯誤。  
  
```vb  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **錯誤識別碼：** BC36629  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用 `As` 子句，將變數宣告為可為 null 的實數值型別。  
  
## <a name="see-also"></a>另請參閱

- [可為 null 的實數值型別](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [區域型別推斷](../../programming-guide/language-features/variables/local-type-inference.md)
