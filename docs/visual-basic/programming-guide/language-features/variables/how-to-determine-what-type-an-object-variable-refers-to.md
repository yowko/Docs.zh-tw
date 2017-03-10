---
title: "How to: Determine What Type an Object Variable Refers To (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TypeOf operator [Visual Basic], determining object variable type"
  - "variables [Visual Basic], object"
  - "object variables, determining type"
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Determine What Type an Object Variable Refers To (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

物件變數包含儲存在任意位置的資料指標 \(Pointer to Data\)。  在執行階段期間可變更該資料的型別。  在任何時間，都可使用 <xref:System.Type.GetTypeCode%2A> 方法來判斷目前的執行階段型別，或使用 [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) 來找出目前的執行階段型別是否與所指定的型別相容。  
  
### 若要判斷物件變數目前參考的確切型別  
  
1.  在物件變數上，呼叫 <xref:System.Object.GetType%2A> 方法來擷取 <xref:System.Type?displayProperty=fullName> 物件。  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  在 <xref:System.Type?displayProperty=fullName> 類別 \(Class\) 上，呼叫共用方法 <xref:System.Type.GetTypeCode%2A> 來擷取該物件型別的 <xref:System.TypeCode> 列舉值。  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     可根據感興趣的列舉型別 \(Enumeration\) 成員 \(例如 `Double`\)，來測試 <xref:System.TypeCode> 列舉值。  
  
### 若要判斷物件變數型別是否與所指定的型別相容  
  
-   將 `TypeOf` 運算子與 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) 搭配使用，即可使用 `TypeOf`...`Is` 運算式來測試物件。  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     如果物件的執行階段型別與所指定的型別相容，則 `TypeOf`...`Is` 運算式會傳回 `True`。  
  
     相容性的條件視所指定的型別是類別、結構或介面而定。  一般而言，如果物件的型別與所指定型別相同、繼承自所指定型別或實作所指定的型別，則型別會相容。  如需詳細資訊，請參閱 [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md)。  
  
## 編譯程式碼  
 注意所指定的型別不可是變數或運算式。  而必須是已定義型別 \(例如類別、結構或介面\) 的名稱。  這包括內建 \(Intrinsic\) 型別，例如 `Integer` 和 `String`。  
  
## 請參閱  
 <xref:System.Object.GetType%2A>   
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Type.GetTypeCode%2A>   
 <xref:System.TypeCode>   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)