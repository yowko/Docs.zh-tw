---
title: 巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594467"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>巢狀函式沒有與委派相容的簽章&#39;&lt;委派名稱&gt;&#39;
Lambda 運算式已被指派至具有相容簽章的委派。 例如，下列程式碼中，委派`Del`有兩個整數參數。  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 如果有一個引數的 lambda 運算式宣告為類型將會引發錯誤`Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **錯誤 ID:** BC36532  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   調整委派定義或指派的 lambda 運算式的簽章是不相容。  
  
## <a name="see-also"></a>另請參閱  
 [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
