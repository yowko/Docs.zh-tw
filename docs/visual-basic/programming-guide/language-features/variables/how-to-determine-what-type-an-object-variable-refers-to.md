---
title: 如何：決定物件變數參考的類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651310"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>如何：決定物件變數參考的類型 (Visual Basic)
物件變數包含儲存在其他位置的資料指標。 在執行階段可以變更該資料的類型。 在任何時刻，您可以使用<xref:System.Type.GetTypeCode%2A>方法，以判斷目前的執行階段類型，或[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來找出是否有目前執行階段型別是使用指定的型別相容。  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>若要判斷的確切型別物件變數目前參考  
  
1.  物件變數上呼叫<xref:System.Object.GetType%2A>方法來擷取<xref:System.Type?displayProperty=nameWithType>物件。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  在<xref:System.Type?displayProperty=nameWithType>類別，呼叫共用的方法<xref:System.Type.GetTypeCode%2A>擷取<xref:System.TypeCode>的物件類型的列舉值。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     您可以測試<xref:System.TypeCode>列舉值，針對任何列舉型別成員感興趣，例如`Double`。  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>若要判斷物件是否與指定的型別相容變數的類型是  
  
-   使用`TypeOf`運算子結合[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)來測試與物件`TypeOf`...`Is`運算式。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     `TypeOf`...`Is`運算式傳回`True`物件的執行階段類型是否與指定的型別相容。  
  
     相容性的條件取決於是否指定的型別是類別、 結構或介面。 一般情況下的類型相容，如果物件為相同的型別、 繼承自或實作指定的型別。 如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 請注意，指定的型別不可以變數或運算式。 它必須是已定義的類型，例如類別、 結構或介面名稱。 這包含內建型別，例如`Integer`和`String`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
