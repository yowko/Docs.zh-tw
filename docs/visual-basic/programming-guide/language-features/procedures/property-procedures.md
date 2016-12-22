---
title: "屬性程序 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Set 陳述式，屬性程序"
  - "Visual Basic 程式碼，程序"
  - "傳回值，屬性程序"
  - "程序，屬性程序"
  - "程序，屬性"
  - "Visual Basic 程式碼，屬性"
  - "程序，呼叫"
  - "屬性 [Visual Basic]，自訂"
  - "屬性程序"
  - "Get 陳述式，屬性程序"
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 屬性程序 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Property 程序是一系列的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 陳述式，可對模組、類別或結構操作自訂屬性。  Property 程序也稱為「*屬性存取子*」\(Property Accessor\)。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供下列 Property 程序：  
  
-   `Get` 程序會傳回屬性的值。  當您存取運算式中的屬性時，會呼叫它。  
  
-   `Set` 程序會設定屬性的值 \(包括物件參考\)。  當您將值指派給屬性時，會呼叫它。  
  
 通常是使用 `Get` 和 `Set` 陳述式成對地定義 Property 程序，但如果屬性是唯讀 \([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)\) 或唯寫 \([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)\)，則可以只定義其中一個程序。  
  
 使用自動實作屬性時，可以省略 `Get` 和 `Set` 程序。  如需詳細資訊，請參閱[Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。  
  
 您可以在類別、結構和模組中定義屬性。  屬性預設值為 `Public`，這表示可從應用程式中任何可存取屬性容器 \(Container\) 的位置呼叫它們。  
  
 如需屬性和變數的比較，請參閱 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)。  
  
## 宣告語法  
 屬性本身是由 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)和 `End Property` 陳述式內封入的程式碼區塊所定義。  在這個區塊中，每一個 Property 程序會顯示為封入宣告陳述式 \(Declaration Statement\) \(`Get` 或 `Set`\) 和相對應 `End` 宣告中的內部區塊。  
  
 宣告屬性和其程序的語法如下：  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers` 可指定多載化 \(Overloading\)、覆寫、共用和遮蔽的存取層級和相關資訊，以及屬性為唯讀或唯寫。  在 `Get` 或 `Set` 中的 `AccessLevel` 可以是要為屬性指定的存取層級更嚴格的所有層級。  如需詳細資訊，請參閱[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)。  
  
### 資料型別  
 屬性資料型別和主要存取層級是定義在 `Property` 陳述式中，而不是 Property 程序中。  屬性只可以有一個資料型別。  例如，不可將屬性定義成儲存 `Decimal` 值，但卻擷取 `Double` 值。  
  
### 存取層級  
 不過，您可定義屬性的主要存取層級，進一步限制在它的其中一個 Property 程序中的存取層級。  例如，可定義 `Public` 屬性，然後定義 `Private Set` 程序。  `Get` 程序仍保持為 `Public`。  只可變更其中一個屬性程序的存取層級，且只可讓它變得比主要存取層級更多約束。  如需詳細資訊，請參閱[How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)。  
  
## 參數宣告  
 使用與宣告 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)的相同方式來宣告每個參數，但傳遞機制必須是 `ByVal`。  
  
 參數清單中每一個參數的語法如下：  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 如果為選擇性參數，您還必須提供預設值做為其宣告的一部分。  用於指定預設值的語法如下：  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## 屬性值  
 在 `Get` 程序中，傳回值會做為屬性值提供給呼叫運算式。  
  
 在 `Set` 程序中，新的屬性值會傳遞到 `Set` 陳述式的參數。  如果您明確地宣告參數，則必須使用與屬性相同的資料型別來進行宣告。  如果您未宣告參數，編譯器會用隱含參數 `Value` 代表指派給該屬性的新值。  
  
## 呼叫語法  
 藉由參考該屬性，隱含地叫用 \(Invoke\) 屬性程序。  您使用屬性名稱的方式與您使用變數名稱的方式相同，除了您必須為所有非選擇性的引數提供值外，還必須將引數清單封入括弧中。  如果未提供引數，您也可以省略括號。  
  
 `Set` 程序的隱含呼叫語法如下：  
  
 `propertyname[(argumentlist)] = expression`  
  
 `Get` 程序的隱含呼叫語法如下：  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### 宣告和呼叫的說明  
 下列屬性會將完整名稱儲存成兩個構成名稱：名字和姓氏。  在呼叫程式碼讀取 `fullName` 時，`Get` 程序會結合這兩個構成名稱，並傳回完整名稱。  在呼叫程式碼指派新的完整名稱時，`Set` 程序會嘗試將新名稱分割成兩個構成名稱。  如果找不到空格，則會將它整個儲存成名字。  
  
 [!CODE [VbVbcnProcedures#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#8)]  
  
 下列範例會示範 `fullName` 之屬性程序的典型呼叫。  
  
 [!CODE [VbVbcnProcedures#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#9)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [How to: Call a Property Procedure](../Topic/How%20to:%20Call%20a%20Property%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)