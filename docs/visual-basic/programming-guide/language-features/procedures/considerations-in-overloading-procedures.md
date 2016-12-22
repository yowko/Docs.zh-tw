---
title: "Considerations in Overloading Procedures (Visual Basic) | Microsoft Docs"
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
  - "signatures, ParamArray arguments"
  - "ParamArray keyword, parameter arrays"
  - "ParamArray keyword, arguments and signatures"
  - "function overloading, implicit overloads for ParamArray"
  - "ParamArray keyword, signatures"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, overloading"
  - "parameters, lists"
  - "function overloading, typeless programming"
  - "typeless programming"
  - "function overloading, restrictions"
  - "arguments [Visual Basic], optional"
  - "optional arguments, overloading"
  - "signatures, procedure"
  - "parameter lists"
  - "parameter arrays, overloading arguments"
  - "Visual Basic code, parameter lists"
  - "procedure overloading, considerations"
  - "Option Explicit statement"
  - "restrictions, overloading procedures"
  - "procedures, parameter lists"
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Considerations in Overloading Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

多載程序時，必須為每一個多載版本使用不同的「*簽章*」\(Signature\)。  這通常表示每一個版本必須指定不同的參數清單。  如需詳細資訊，請參閱[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)中的＜不同的簽章＞一節。  
  
 您可以用 `Sub` 程序多載 `Function` 程序，反之亦然，除非它們的簽章不同。  兩個多載不能只有一個多載具有傳回值，而另一個沒有傳回值。  
  
 您可以使用多載程序的方法和相同的限制來多載屬性。  然而，您無法以屬性來多載程序，反之亦然。  
  
## 多載版本的替代方案  
 您有時會有多載版本的替代方案，特別是出現選擇性引數或其數目可以變動時。  
  
 請記住，並非所有語言都一定支援選擇性引數，且參數陣列只能用於 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  如果您正在撰寫程序，且可能會從以數種不同語言之其中一種所撰寫的程式碼中呼叫該程序時，多載版本就可以提供最大的彈性。  
  
### 多載和選擇性引數  
 當呼叫程式碼可以選擇性地提供或省略一或多個引數時，即可定義多個多載版本或使用選擇性參數。  
  
#### 多載版本的使用時機  
 在下列情況下，您可以考慮定義一系列的多載版本：  
  
-   根據呼叫程式碼是否提供選擇性引數，程序碼的邏輯會有顯著的差異。  
  
-   程序碼無法穩定地測試呼叫程式碼是否已提供選擇性引數。  例如，若呼叫程式碼不能提供可能的候選引數來取代預設值，就會發生這種情況。  
  
#### 選擇性參數的使用時機  
 在下列情況中，您可能想使用一或多個選擇性參數：  
  
-   如果呼叫程式碼不提供選擇性引數，則唯一要做的動作是將參數設定為預設值。  在此情況下，若以一或多個 `Optional` 參數定義單一版本，程序碼可以較為單純。  
  
 如需詳細資訊，請參閱[Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)。  
  
### 多載和參數陣列  
 當呼叫程式碼可傳遞可變的引數數目時，即可定義多個多載版本或使用參數陣列。  
  
#### 多載版本的使用時機  
 在下列情況下，您可以考慮定義一系列的多載版本：  
  
-   您瞭解呼叫程式碼只會將少量的值傳給參數陣列。  
  
-   根據呼叫程式碼傳遞的值數目，程序碼的邏輯會有顯著的差異。  
  
-   呼叫程式碼可傳遞不同資料型別的值。  
  
#### 參數陣列的使用時機  
 在下列情況下，最好使用 `ParamArray` 參數：  
  
-   您不能預測呼叫程式碼能傳遞給參數陣列的值數目，該數目可能很大。  
  
-   程式邏輯本身會逐一查看所有呼叫程式碼傳遞的值，依序進行基本上相同的運算。  
  
 如需詳細資訊，請參閱[Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)。  
  
## 選擇性參數的隱含多載  
 有 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) 參數的程序等於兩個多載化程序，其中一個有選擇性參數，另外一個則沒有。  您無法以對應至任一情況的參數清單來多載此類程序。  下面宣告可說明這點。  
  
 [!CODE [VbVbcnProcedures#58](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#58)]  
  
 [!CODE [VbVbcnProcedures#60](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#60)]  
  
 [!CODE [VbVbcnProcedures#61](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#61)]  
  
 對於擁有超過一個選擇性參數的程序而言，會有一組類似上述範例邏輯的隱含多載。  
  
## ParamArray 參數的隱含多載  
 編譯器 \(Compiler\) 將具有 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 參數的程序視為含有不確定數目的多載，不同之處在於呼叫程式碼傳遞至參數陣列的項目，如下所示：  
  
-   適用於呼叫程式碼未將引數提供給 `ParamArray` 時的多載。  
  
-   適用於呼叫程式碼提供 `ParamArray` 元素型別之一維陣列時的多載。  
  
-   對每一個正整數而言，當呼叫程式碼提供該數目之引數的一個多載傳遞，每一個都是 `ParamArray` 元素型別。  
  
 下列宣告可說明這些隱含多載：  
  
 [!CODE [VbVbcnProcedures#68](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#68)]  
  
 [!CODE [VbVbcnProcedures#70](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#70)]  
  
 對於這類擁有採用一維陣列當做參數陣列的參數清單之程序，您無法多載。  然而，您可以使用其他隱含多載的簽章。  下面宣告可說明這點。  
  
 [!CODE [VbVbcnProcedures#71](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnProcedures#71)]  
  
## 不具型別程式設計 \- 多載化的替代方案  
 如果您想要讓呼叫程式碼來將不同資料型別傳遞至參數，另一個方法是不具型別的程式設計。  您可以使用 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或 [\/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) 編譯器選項，將型別檢查參數設定為 `Off`。  之後即不需宣告參數的資料型別。  但是，與多載化比較之下，這個方法有下列缺點：  
  
-   無型別程式設計產生較沒有效率的執行程式碼。  
  
-   程序必須測試它預期傳遞的每一個資料型別。  
  
-   如果呼叫程式碼傳遞了一個該程序不支援的資料型別，編譯器無法發出錯誤信號。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../Topic/How%20to:%20Call%20an%20Overloaded%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)