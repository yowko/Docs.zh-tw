---
title: "Troubleshooting Procedures (Visual Basic) | Microsoft Docs"
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
  - "troubleshooting Visual Basic, procedures"
  - "procedures, troubleshooting"
  - "Visual Basic code, procedures"
  - "troubleshooting procedures"
  - "procedures, about procedures"
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Troubleshooting Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

本頁列出一些使用程序時所發生的常見問題。  
  
## 從 Function 程序傳回陣列型別  
 如果 `Function` 程序傳回陣列資料型別，則不可使用 `Function` 名稱將值儲存在陣列項目中。  如果您嘗試這麼做，編譯器會將它解譯為對 `Function` 的呼叫。  下列範例會產生編譯器錯誤。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 陳述式 \(Statement\) `allOnes(i) = 1` 會產生編譯器錯誤，原因是它似乎呼叫的是含有資料型別錯誤之引數的 `allOnes` \(單一 `Integer`，而非 `Integer` 陣列\)。  陳述式 `Return allOnes()` 會產生編譯器錯誤，原因是它可能呼叫了不含引數的 `allOnes`。  
  
 **正確方法：**若要修改所傳回的陣列項目，請將內部陣列定義成區域變數。  下列範例會進行編譯，且不會發生錯誤。  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## 程序呼叫並未修改引數的值  
 如果想要在呼叫程式碼中允許程序變更程式設計項目所對應的引數，則必須以傳址 \(By Reference\) 方式進行傳遞。  但即使是以傳值 \(By Value\) 方式傳遞程序，該程序仍可存取參考型別 \(Reference Type\) 引數的項目。  
  
-   **對應變數**：  若要允許程序取代對應變數項目本身的值，則程序必須宣告參數 [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。  而且，呼叫程式碼不得將引數封入括弧中，原因是這麼做會覆寫 `ByRef` 傳遞機制。  
  
-   **型別參考項目**：  如果宣告參數 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，則程序無法修改對應變數項目本身。  但是，如果引數是參考型別，即使它無法取代變數的值，仍可以修改其指向的物件成員。  例如，如果引數是陣列變數，程序就無法指派新的陣列給它，但可以變更其一個或多個項目。  更改的項目會反映在呼叫程式碼中的陣列變數。  
  
 下列範例會定義兩個以傳值方式取得陣列變數，並在其項目上作業的程序。  `increase` 程序只會將每個項目加一。  程序 `replace` 會將新的陣列指派給參數 `a()`，然後每個項目都加一。  但是，重新指派並不會影響呼叫程式碼中的對應陣列變數，因為 `a()` 是以 `ByVal` 方式宣告。  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 下列範例會進行 `increase` 和 `replace` 的呼叫：  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 第一個 `MsgBox` 呼叫顯示 "After increase\(n\): 11, 21, 31, 41"。  因為 `n` 是參考型別，所以即使 `increase` 是以 `ByVal` 方式傳遞，仍可變更其成員。  
  
 第二個 `MsgBox` 呼叫顯示 "After replace\(n\): 11, 21, 31, 41"。  因為 `n` 是以 `ByVal` 方式傳遞，所以 `replace` 無法透過指派新陣列來修改變數 `n`。  當 `replace` 建立新陣列執行個體 \(Instance\) `k`，並且將它指派給區域變數 `a` 時，會遺失呼叫程式碼所傳入之 `n` 的參考。  當它增加 `a` 的成員時，只會影響區域陣列 `k`。  
  
 **正確方法：**若要修改基礎變數元素本身，請以傳址方式進行傳遞。  下列範例會顯示 `replace` 宣告中的變更，這個變更允許以呼叫程式碼中的另一個陣列來取代某個陣列。  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## 無法定義多載  
 如果想要定義程序的多載版本，則必須使用相同名稱，但不同的簽章。  如果編譯器無法辨識您的宣告與具有相同簽章的多載，則會產生錯誤。  
  
 程序的「*簽章*」\(Signature\) 是由程序名稱和參數清單所決定。  每個多載的名稱都必須與所有其他多載的名稱相同，但簽章中的元件至少有一個必須與其他的多載不同。  如需詳細資訊，請參閱[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
 下列項目 \(即使它們屬於參數清單\) 不是程序簽章的元件：  
  
-   程序修飾詞關鍵字，例如 `Public`、`Shared` 和 `Static`  
  
-   參數名稱。  
  
-   參數修飾詞關鍵字，如 `ByRef` 和 `Optional`  
  
-   傳回值的資料型別 \(轉換運算子除外\)。  
  
 只改變上述一或多個項目，並無法多載程序。  
  
 **正確方法：**若要定義程序多載，則必須改變簽章。  因為您必須使用相同的名稱，所以必須改變參數的數目、順序或資料型別。  在泛型程序中，您可改變型別參數的數目。  在轉換運算子 \([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)\) 中，可改變傳回型別。  
  
### 具有選擇性和 ParamArray 引數的多載解析  
 如果多載化 \(Overloading\) 具有一或多個 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) 參數或 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 參數的程序，則必須避免複製任何「*隱含多載*」\(Implicit Overload\)。  如需詳細資訊，請參閱[Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)。  
  
## 呼叫錯誤的多載程序版本  
 如果程序具有數個多載版本，則應熟悉其所有的參數清單，並了解 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 如何解析多載間的呼叫。  否則，您可能會呼叫並不想要的多載。  
  
 當您已決定想要呼叫的多載時，請仔細觀察下列規則：  
  
-   提供正確數目的引數，並依正確的順序排序。  
  
-   最理想的狀況是，引數的資料型別與對應的參數完全相同。  在任何情況下，每個引數的資料型別都必須擴展成其對應參數的資料型別。  即使 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設為 `Off` 也是如此。  如果多載需要從引數清單中進行任何縮小轉換，則不能夠呼叫該多載。  
  
-   如果提供需要擴展的引數，請讓其資料型別盡可能地與對應的參數資料型別相近。  如果兩個或多個多載接受您的引數資料型別，則編譯器會解析您對於多載的呼叫，這個多載會呼叫最少擴展量。  
  
 準備引數時，您可使用 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)轉換關鍵字，以減少資料型別不符合的機會。  
  
### 多載解析失敗  
 呼叫多載程序時，編譯器會嘗試排除所有多載，但只留下一個多載。  如果成功的話，它會解析該多載的呼叫。  如果排除了所有多載，或如果無法將合格的多載減少成單一候選項，則會產生錯誤。  
  
 下列範例會說明多載解析 \(Overload Resolution\) 的處理過程。  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 在第一個呼叫中，因為第一個引數的型別 \(`Short`\) 會縮小對應參數的型別 \(`Byte`\)，所以編譯器會排除第一個多載。  然後，因為第二個多載中的每個引數型別 \(`Short` 和 `Single`\) 都擴展成第三個多載中的對應型別 \(`Integer` 和 `Single`\)，所以會排除第三個多載。  第二個多載需要較少的擴展，因此編譯器會將它用於呼叫。  
  
 在第二個呼叫中，編譯器無法以縮小為基礎來排除任何多載。  因為它可呼叫較不需要擴展引數型別的第二個多載，所以它會用第一個呼叫中的相同理由來排除第三個多載。  不過，編譯器無法在第一個與第二個多載之間進行解析。  每個多載都會有一個定義的參數型別，此型別會擴展為其他多載中的對應型別 \(`Byte` 至 `Short`，但 `Single` 至 `Double`\)。  編譯器因此產生多載解析錯誤。  
  
 **正確方法：**若要明確呼叫多載程序，請使用 [CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)讓引數資料型別與參數型別相符。  下列範例會顯示對於 `z` 的呼叫，其可強制解析第二個多載。  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### 具有選擇性和 ParamArray 引數的多載解析  
 如果程序的兩個多載擁有相同的簽章，但最後一個參數在某個程序中宣告為 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)，而在另一個程序中宣告為 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)，則編譯器會依據最接近的符合項目來解析該程序的呼叫。  如需詳細資訊，請參閱[Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)。  
  
## 請參閱  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [函式程序](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [屬性程序](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)