---
title: "Object Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Object"
  - "vb.Variant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object variables, Object type"
  - "data types [Visual Basic], assigning"
  - "Object data type"
  - "Object data type, reference"
ms.assetid: 61ea4a7c-3b3d-48d4-adc4-eacfa91779b2
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Object Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

保留參考物件的位址。  您可以將任何參考型別 \(字串、陣列、類別或介面\) 指派給 `Object` 變數。  `Object` 變數也可參考任何實值型別的資料 \(數字、`Boolean`、`Char`、`Date`、結構或列舉\)。  
  
## 備註  
 `Object` 資料型別可指向任何資料型別的資料，包含應用程式所辨識的任何物件執行個體。  在編譯時期，如果不知道變數可能指向的資料型別，則請使用 `Object`。  
  
 `Object` 的預設值為 `Nothing` \(null 參考\)。  
  
## 資料型別  
 您可以將任何資料型別的變數、常數或運算式指派至 `Object` 變數。  若要判斷 `Object` 變數目前所參考的資料型別，可使用 <xref:System.Type?displayProperty=fullName> 類別的 <xref:System.Type.GetTypeCode%2A> 方法。  下列範例將說明這點。  
  
```  
Dim myObject As Object  
' Suppose myObject has now had something assigned to it.  
Dim datTyp As Integer  
datTyp = Type.GetTypeCode(myObject.GetType())  
```  
  
 `Object` 資料型別就是參考型別。  不過，Visual Basic 在參考實值型別的資料時，會將 `Object` 變數視為實值型別。  
  
## 儲存區  
 無論它所參考的資料型別為何，`Object` 變數都不會包含資料值本身，而是值的指標。  它在電腦記憶體中所佔的空間為 4 個位元組，但這並不包括儲存表示變數值的資料。  由於使用指標來找出資料的程式碼之故，存放實值型別的 `Object` 變數會比有明確型別的變數在存取方面要來得稍慢些。  
  
## 程式設計提示  
  
-   **Interop 考量：**：如果使用的是未針對 .NET Framework 撰寫的元件 \(例如 Automation 或 COM 物件\)，請記住其他環境中的指標型別與 Visual Basic `Object` 型別不相容。  
  
-   **效能**：使用 `Object` 型別宣告的變數能夠包含任何物件的參考。  不過，在此類變數上叫用方法或屬性時，一律會在執行階段時造成「*晚期繫結*」\(Late Binding\)。  若要在編譯時期強制「*早期繫結*」\(Early Binding\) 和較佳的效能，請使用特定類別名稱來宣告變數，或將它轉換成特定資料型別。  
  
     當您宣告物件變數時，請試著使用特定的類別型別 \(例如，<xref:System.OperatingSystem>\)，而非通用 `Object` 型別。  您也應使用最適合的特定類別，例如 <xref:System.Windows.Forms.TextBox> 而非 <xref:System.Windows.Forms.Control>，如此一來您就可存取其屬性和方法。  您通常可使用 \[**物件瀏覽器**\] 中的 \[**類別**\] 清單，找出可用的類別名稱。  
  
-   **擴展：**：所有資料型別和所有參考型別都會擴展成 `Object` 資料型別。  這表示您可以將任何類型轉換成 `Object`，而不會發生 <xref:System.OverflowException?displayProperty=fullName> 錯誤。  
  
     不過，如果轉換實值型別與 `Object`，則 Visual Basic 會執行稱為「*Boxing*」和「*Unboxing*」的作業，這些作業會讓執行速度變慢。  
  
-   **型別字元**：`Object` 沒有常值型別字元或識別項型別字元。  
  
-   **架構型別。**.NET Framework 中的對應型別為 <xref:System.Object?displayProperty=fullName> 類別。  
  
## 範例  
 下列範例會說明指向物件執行個體的 `Object` 變數。  
  
```  
Dim objDb As Object  
Dim myCollection As New Collection()  
' Suppose myCollection has now been populated.  
objDb = myCollection.Item(1)  
```  
  
## 請參閱  
 <xref:System.Object>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [How to: Determine Whether Two Objects Are Related](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [How to: Determine Whether Two Objects Are Identical](../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)