---
title: 如何：決定物件變數參考的類型
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: b3778a170759f685db78e7dcde219138196f9eca
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344191"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a>如何：決定物件變數參考的類型 (Visual Basic)

物件變數包含儲存在其他位置之資料的指標。 該資料的類型可能會在執行時間變更。 您隨時都可以使用 <xref:System.Type.GetTypeCode%2A> 方法來判斷目前的執行時間型別，或使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來找出目前的執行時間型別是否與指定的型別相容。

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a>判斷物件變數目前所參考的確切型別

1. 在物件變數上，呼叫 <xref:System.Object.GetType%2A> 方法來取出 <xref:System.Type?displayProperty=nameWithType> 物件。

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. 在 <xref:System.Type?displayProperty=nameWithType> 類別上，呼叫 shared 方法 <xref:System.Type.GetTypeCode%2A>，以取得物件類型的 <xref:System.TypeCode> 列舉值。

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    您可以針對任何想要的列舉成員（例如 `Double`）測試 <xref:System.TypeCode> 列舉值。

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a>判斷物件變數的類型是否與指定的類型相容

- 使用 `TypeOf` 運算子搭配[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)來測試具有 `TypeOf``Is` 運算式的物件。

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    `TypeOf`...`Is` 如果物件的執行時間類型與指定的類型相容,`True`則運算式會傳回。

    相容性的準則取決於指定的類型是否為類別、結構或介面。 一般而言，如果物件的類型與相同、繼承自或實作為指定的類型，則類型是相容的。 如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。

## <a name="compile-the-code"></a>編譯程式碼

請注意，指定的類型不可以是變數或運算式。 它必須是已定義類型的名稱，例如類別、結構或介面。 這包括內部類型，例如 `Integer` 和 `String`。

## <a name="see-also"></a>請參閱

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
