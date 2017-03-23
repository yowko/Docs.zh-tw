---
title: "Double Data Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Double"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "identifier type characters, #"
  - "trailing zeros"
  - "real numbers"
  - "trailing 0 characters"
  - "0 characters, trailing"
  - "literal type characters, R"
  - "data types [Visual Basic], assigning"
  - "Double data type [Visual Basic]"
  - "# identifier type character"
  - "double-precision numbers"
  - "floating-point numbers, Double data type"
  - "R literal type character"
  - "zeros, trailing"
  - "Double data type"
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# Double Data Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

存放帶正負號的 IEEE 64 位元 \(8 個位元組\) 雙精度浮點數值 \(Floating\-Point Number\)，其值範圍在負值方面是從 \-1.79769313486231570E\+308 至 \-4.94065645841246544E\-324，在正值方面則是從 4.94065645841246544E\-324 至 1.79769313486231570E\+308。  雙精度數字會儲存實數的近似值。  
  
## 備註  
 `Double` 資料型別會針對數字提供最大和最小的可能大小。  
  
 `Double` 的預設值為 0。  
  
## 程式設計提示  
  
-   **精確度：** 使用浮點數值 \(Floating\-Point Number\) 時，請記住它們在記憶體中不一定都會有精確的表示。  這樣可能會因為某些作業，例如值比較和 `Mod` 運算子，而導致無法預期的結果。  如需詳細資訊，請參閱 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
-   **結尾的零：** 浮點資料型別沒有結尾零字元的任何內部表示。  例如，它們無法區分 4.2000 與 4.2。  因此，當您顯示或列印浮點數值時，結尾零字元不會出現。  
  
-   **型別字元。** 將常值型別字元 `R` 附加到常值會強制其成為 `Double` 資料型別。  例如，如果整數值後面是 `R`，則值會變更為 `Double`。  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     將識別項型別字元 `#` 附加到任何識別項，會強制其成為 `Double`。  在下列範例中，變數 `num` 的型別為 `Double`：  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **架構型別。** 在 .NET Framework 中對應的型別為 <xref:System.Double?displayProperty=fullName> 結構。  
  
## 請參閱  
 <xref:System.Double?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)   
 [Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)