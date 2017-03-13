---
title: "Local Type Inference (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "local type inference"
  - "vb.TypeInfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Option Infer statement"
  - "local type inference [Visual Basic]"
  - "implicitly-typed local variables [Visual Basic]"
  - "variables [Visual Basic], type inference"
  - "inference [Visual Basic]"
  - "type inference [Visual Basic]"
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 43
---
# Local Type Inference (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Visual Basic 編譯器會使用「*型別推斷*」\(Type Inference\) 來判斷未使用 `As` 子句宣告之區域變數的資料型別。  編譯器是根據初始化運算式的型別推斷變數的型別。  這可以讓您宣告變數而不用明確陳述型別，如同下列範例所示。宣告的結果是，`num1` 和 `num2` 都會變成強型別的整數。  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
  
> [!NOTE]
>  如果您不要前述範例中 `num2` 的型別為 `Integer`，則可指定其他型別，方法是使用 `Dim num3 As Object = 3` 或 `Dim num4 As Double = 3` 之類的宣告。  
  
 區域型別推斷適用於程序層次，  不能用在模組層次 \(在類別、結構、模組或介面中，但程序和區塊除外\) 宣告變數。  如果上一個範例中的 `num2` 是類別欄位而非程序中的區域變數，則宣告會造成 `Option Strict` 為 On 的錯誤，並且會將 `num2` 分類為 `Object` 且 `Option Strict` 為 Off。  同樣地，區域型別推斷不適用於宣告為 `Static` 的程序層級變數。  
  
## 型別推斷和晚期繫結的比較  
 使用型別推斷的程式碼，類似於依賴晚期繫結 \(Late Binding\) 的程式碼。  但是，型別推斷會使變數成為強型別，而不是維持 `Object`。  編譯器使用變數的初始設定式，在編譯時期判斷變數的型別以產生早期繫結程式碼。  在前述範例中，`num2` 與 `num1` 相同，型別都是 `Integer`。  
  
 早期繫結變數的行為與晚期繫結變數不同，晚期繫結的型別只有在執行階段是已知的。  及早知悉型別可以讓編譯器在執行之前識別問題、準確配置記憶體，以及執行其他最佳化作業。  早期繫結也可以讓 Visual Basic 整合式開發環境 \(IDE\) 提供物件成員的相關 IntelliSense 說明。  此外，使用早期繫結也能提供較佳的效能。  這是因為儲存在晚期繫結變數中的所有資料必須包裝為型別 `Object`，而在執行階段存取此型別的成員會使程式變得更慢。  
  
## 範例  
 區域變數未使用 `As` 子句宣告並初始化時，便會發生型別推斷。  編譯器會使用所指派初始值的型別，做為變數的型別。  例如，以下每一行程式碼都會宣告一個 `String` 型別的變數。  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 下列程式碼示範建立整數陣列的兩個對等方式。  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 使用型別推斷來判斷迴圈控制變數的型別相當方便。  在下列程式碼中，編譯器推斷 `number` 是 `Integer`，因為前述範例的 `someNumbers2` 是整數陣列。  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 區域型別推斷可以用在 `Using` 陳述式中，用來建立資源名稱的型別，如下列範例所示。  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 變數的型別也可以根據函式的傳回值來推斷，如下列範例所示。  `pList1` 和 `pList2` 都是處理序陣列，因為 `Process.GetProcesses` 會傳回處理序陣列。  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## Option Infer  
 `Option Infer`可讓您指定特定的檔案是否允許區域型別推斷。  若要啟用或封鎖選項，請在檔案開頭輸入下列其中一個陳述式。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 如果您沒有在程式碼中指定 `Option Infer` 的值，則編譯器預設值為 `Option Infer On`。  若是從 [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb-orcas-long-md.md)] 或舊版升級的專案，編譯器預設值為 `Option Infer Off`。  
  
 如果檔案中設定的 `Option Infer` 值與 IDE 或命令列中設定的值相衝突，檔案中的值有優先權。  
  
 如需詳細資訊，請參閱 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)。  
  
## 限制  
 型別推斷只能用在非靜態區域變數，無法用於判斷類別欄位、屬性或函式的型別。  
  
## 請參閱  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [For Each...Next 陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [For...Next 陳述式](../../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [\/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)