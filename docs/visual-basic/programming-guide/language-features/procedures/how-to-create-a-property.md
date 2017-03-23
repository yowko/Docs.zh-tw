---
title: "How to: Create a Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "procedures, defining"
  - "Visual Basic code, procedures"
  - "Visual Basic code, properties"
  - "properties [Visual Basic]"
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

透過封入 `Property` 陳述式 \(Statement\) 與 `End Property` 陳述式來定義屬性。  在這個定義內，可定義 `Get` 程序和 \(或\) `Set` 程序。  所有屬性程式碼都落在這些程序內。  
  
 `Get` 程序會擷取屬性值，而 `Set` 程序會儲存值。  如果想要屬性具有讀取\/寫入存取權，則必須定義這兩個程序。  若為唯讀屬性，則只定義 `Get`，而若為唯寫屬性，則只定義 `Set`。  
  
### 若要建立屬性  
  
1.  在任何屬性或程序外部，使用後面緊接 `End Property` 陳述式的 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)。  
  
2.  如果屬性採用參數，請在 `Property` 關鍵字後面緊接著程序名稱，然後是以括弧括住的參數清單。  
  
3.  在括弧後面緊接著 `As` 子句，以指定屬性值的資料型別。  即使是唯寫屬性，也必須指定資料型別。  
  
4.  適當地加入 `Get` 和 `Set` 程序。  請參閱下列指示。  
  
### 若要建立用來擷取屬性值的 Get 程序  
  
1.  在 `Property` 與 `End Property` 陳述式之間，寫入 [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)，後面緊接 `End Get` 陳述式。  您不需要定義 `Get` 程序的任何參數。  
  
2.  放置程式碼陳述式，以擷取 `Get` 和 `End Get` 陳述式間的屬性值。  除了產生和傳回屬性值外，這個程式碼可包含其他計算和資料操作。  
  
3.  使用 `Return` 陳述式，將屬性值傳回給呼叫程式碼。  
  
 對於讀寫屬性和唯讀屬性，您必須撰寫 `Get` 程序。  對於唯寫屬性，則不得定義 `Get` 程序。  
  
### 若要建立用來寫入屬性值的 Set 程序  
  
1.  在 `Property` 與 `End Property` 陳述式之間，寫入 [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)，後面緊接 `End Set` 陳述式。  
  
2.  在 `Set` 陳述式中，請在 `Set` 關鍵字後面緊接著以括弧括住的參數清單。  這個參數清單至少必須包含呼叫程式碼所傳遞之值的值參數。  這個值參數的預設名稱是 `Value`，但可視情況使用不同的名稱。  值參數的資料型別必須與屬性本身相同。  
  
3.  放置程式碼陳述式，以將值儲存在 `Set` 與 `End Set` 陳述式間的屬性中。  除了驗證和儲存屬性值外，這個程式碼可包含其他計算和資料操作。  
  
4.  使用值參數來接受 \(Accept\) 呼叫程式碼所提供的值。  您可直接將這個值儲存在指派陳述式 \(Assignment Statement\) 中，或將它用於運算式中，以計算所要儲存的內部值。  
  
 對於讀寫屬性和唯寫屬性，您必須撰寫 `Set` 程序。  對於唯讀屬性，則不得定義 `Set` 程序。  
  
## 範例  
 下列範例建立讀取\/寫入屬性，以將完整名稱儲存成兩個構成名稱：名字和姓氏。  在呼叫程式碼讀取 `fullName` 時，`Get` 程序會結合這兩個構成名稱，並傳回完整名稱。  在呼叫程式碼指派新的完整名稱時，`Set` 程序會嘗試將新名稱分割成兩個構成名稱。  如果找不到空格，則會將它整個儲存成名字。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 下列範例會示範 `fullName` 之屬性程序的典型呼叫。  第一個呼叫會設定屬性值，而第二個呼叫則會擷取該值。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)