---
title: "Value Types and Reference Types | Microsoft Docs"
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
  - "reference data types"
  - "reference types"
  - "value types"
  - "value data types"
  - "types [Visual Basic]"
  - "data types [Visual Basic], value types"
  - "data types [Visual Basic], reference types"
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Value Types and Reference Types
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 資料型別會實作其分類為基礎。  根據特定型別的變數是否儲存自己專屬的資料或資料指標，就能將 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 資料型別加以分類。  如果它會儲存自己專屬的資料，則為「*實值型別*」\(Value Type\)。如果它會儲存記憶體中別處資料的指標，則為「*參考型別*」\(Reference Type\)。  
  
## 實值型別  
 若資料型別是在其本身的記憶體配置中存放資料，資料型別就屬於「*實值型別*」\(Value Type\)。  實值型別包含下列項目：  
  
-   所有的數字資料型別  
  
-   `Boolean`、`Char` 和 `Date`  
  
-   所有結構 \(即使其成員也屬於參考型別的結構\)  
  
-   列舉型別 \(Enumeration\)，因為其基礎型別一定是 `SByte`、`Short`、`Integer`、`Long`、`Byte`、`UShort`、`UInteger` 或 `ULong`  
  
 每個結構是實值型別，即使它包含參考型別成員。  基於這個理由，值輸入如`Char`和`Integer`由實作。NET Framework 的結構。  
  
 您可以使用保留的關鍵字 \(例如 `Decimal`\) 宣告實值型別。  您也可以使用 `New` 關鍵字來初始化實值型別。  若型別具有包含參數的建構函式 \(Constructor\) 則特別適用。  <xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> 建構函式是這種範例中的一個，它會依據提供的組件建置新的 `Decimal` 值。  
  
## 參考型別  
 「*參考型別*」\(Reference Type\) 包含存放在其他記憶體配置中資料的指標。  參考型別包含下列項目：  
  
-   `String`  
  
-   所有陣列 \(即使其元素也屬於實值型別的陣列\)  
  
-   類別型別，例如 <xref:System.Windows.Forms.Form>  
  
-   委派  
  
 類別是「*參考型別*」\(Reference Type\)。  基於這個原因，像 `Object` 和 `String` 這類的參考型別是由 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 類別支援。  請注意，每個陣列都是參考型別，即使其成員屬於實值型別亦同。  
  
 因為每個參考型別代表著一個基礎。NET Framework 類別，您必須使用[New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字，當您將它初始化。  下列陳述式會進行陣列初始化。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## 不是型別的元素  
 下列程式設計項目不能限定型別，因為您無法指定任何一個型別做為宣告項目的資料型別：  
  
-   命名空間  
  
-   模組  
  
-   事件  
  
-   屬性和程序  
  
-   變數、常數和欄位  
  
## 使用物件資料型別  
 您可以將參考型別或實值型別指派至 `Object` 資料型別的變數。  `Object` 變數存放的永遠是資料的指標，而非資料本身。  但是如果您將實值型別指派給 `Object` 變數，則此變數看起來就像是存放其本身的資料一般。  如需詳細資訊，請參閱 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 您可以找出是否`Object`變數，會藉由傳遞給它做為參考型別或實值型別<xref:Microsoft.VisualBasic.Information.IsReference%2A>中的方法<xref:Microsoft.VisualBasic.Information>類別的<xref:Microsoft.VisualBasic?displayProperty=fullName>命名空間。  如果 `Object` 變數的內容代表參考型別，則 <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> 會傳回 `True`。  
  
## 請參閱  
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)