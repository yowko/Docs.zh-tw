---
title: 無法從這些引數推斷類型參數的資料類型
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 81535e3272eaed587288c26c4a4b9649467abed8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963556"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>無法從這些引數推斷類型參數的資料類型
無法從這些引數推斷類型參數的資料類型。 明確指定資料類型或許可以更正這個錯誤。  
  
 多載解析失敗時，會發生這個錯誤。 它會顯示為附屬訊息，說明為什麼排除特定多載候選項目。 錯誤訊息說明編譯器無法使用類型推斷來尋找類型參數的資料類型。  
  
> [!NOTE]
> 當無法指定引數時 (例如，針對查詢運算式中的查詢運算子)，會顯示不含第二句的錯誤訊息。  
  
 下列程式碼示範這個錯誤。  
  
```vb  
Module Module1  
  
    Sub Main()  
  
        '' Not Valid.  
        'OverloadedGenericMethod("Hello", "World")  
  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T)(ByVal x As String,   
                                      ByVal y As InterfaceExample(Of T))  
    End Sub  
  
    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,   
                                         ByVal y As InterfaceExample(Of R))  
    End Sub  
  
End Module  
  
Interface InterfaceExample(Of T)  
End Interface  
```  
  
 **錯誤識別碼:** BC36647 和 BC36644  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 您可以指定一個或多個類型參數的資料類型，而不是依賴類型推斷。  
  
## <a name="see-also"></a>另請參閱

- [寬鬆委派轉換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Visual Basic 中的類型轉換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
