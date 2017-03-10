---
title: "User-Defined Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "UserDefined"
  - "UDT"
  - "vb.UDT"
  - "User-Defined"
  - "vb.UserDefined"
  - "vb.User-Defined"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "user-defined data types, Visual Basic"
  - "user-defined types"
  - "structures, as user-defined data types"
  - "user-defined types, Visual Basic"
  - "user-defined types, structure declaration"
  - "user-defined types, structures in Visual Basic"
  - "user-defined data types, structure declaration"
  - "data types [Visual Basic], assigning"
  - "Structure statement"
  - "data types [Visual Basic], user-defined"
  - "user-defined data types, structures in Visual Basic"
  - "user-defined data types"
  - "types [Visual Basic], user-defined"
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# User-Defined Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

保留您定義之格式的資料。  `Structure` 陳述式 \(Statement\) 會定義格式。  
  
 舊版的 Visual Basic 支援使用者定義型別 \(UDT\)。  目前的版本會將 UDT 展開成「*結構*」\(Structure\)。  結構是各種資料型別之一個或多個「*成員*」\(Member\) 的串連。  Visual Basic 會將結構視為單一單位，但您也能個別存取其成員。  
  
## 備註  
 當您需要將各種資料型別結合成單一單位，或是沒有適合所需的基礎資料型別 \(Elementary Data Type\) 時，請定義和使用結構資料型別。  
  
 結構資料型別的預設值，是由其每個成員的預設值組合所組成。  
  
## 宣告格式  
 結構宣告是以 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)開始，並以 `End` `Structure` 陳述式結束。  `Structure` 陳述式會提供結構的名稱，這同時也是由結構定義的資料型別識別項。  程式碼的其他部分可以使用這個識別項，將變數、參數和函式傳回值宣告為這個結構的資料型別。  
  
 `Structure` 陳述式和 `End` `Structure` 陳述式之間的宣告可定義結構成員。  
  
## 成員存取層級  
 您必須使用 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) 或指定存取層級的陳述式 \(例如 [Public](../../../visual-basic/language-reference/modifiers/public.md)、[Friend](../../../visual-basic/language-reference/modifiers/friend.md) 或 [Private](../../../visual-basic/language-reference/modifiers/private.md)\) 來宣告每個成員。  如果您使用 `Dim` 陳述式，則存取層級會預設為公用 \(Public\)。  
  
## 程式設計提示  
  
-   **記憶體消耗量**： ：和所有複合資料型別一樣，將成員的表面儲存配置加總起來不一定就是結構的總記憶體耗用量。  除此之外，您也不能就將記憶體中的儲存順序視為與您宣告的順序相同。  如果需要控制結構的儲存體配置，可將 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性 \(Attribute\) 套用到 `Structure` 陳述式。  
  
-   **Interop 考量：** ：如果您正在使用的元件不是針對 .NET Framework 所撰寫的 \(例如 Automation 或 COM 物件\)，請記住，其他環境中的使用者定義型別會與 Visual Basic 結構型別不相容。  
  
-   **擴展：** ：不會與任何結構資料型別進行自動轉換。  您可以使用 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)，在結構上定義轉換運算子，也可以將每一個轉換運算子宣告成 `Widening` 或 `Narrowing`。  
  
-   **型別字元。** ：結構資料型別沒有常值 \(Literal\) 型別字元或識別項型別字元。  
  
-   **架構型別。** ：.NET Framework 中沒有對應的型別。  所有結構都繼承自 .NET Framework 類別 <xref:System.ValueType?displayProperty=fullName>，但沒有個別結構對應於 <xref:System.ValueType?displayProperty=fullName>。  
  
## 範例  
 下列的開發架構將顯示結構宣告的大綱。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## 請參閱  
 <xref:System.ValueType>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)