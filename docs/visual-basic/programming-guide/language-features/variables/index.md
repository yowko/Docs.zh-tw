---
title: "Variables in Visual Basic | Microsoft Docs"
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
  - "variables [Visual Basic]"
  - "values [Visual Basic], storing"
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Variables in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當您利用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 執行計算時，通常都會需要儲存值。  例如，您可能想計算數個值，將它們互相比較，並根據比較的結果執行不同的運算。  如果想要進行比較，您需要保留這些值。  
  
## 使用方式  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 就像大多數的程式語言一樣，是以變數儲存值。  「*變數*」\(Variable\) 都具有名稱 \(您用來參考變數所包含值的文字\)。  變數也都具有資料型別 \(決定變數可以儲存何種資料\)。  如果變數需要儲存一組關係密切的資料項目索引，則可代表一個陣列。  
  
 區域型別推斷可讓您宣告變數卻不需要明確表明其資料型別，  而是讓編譯器 \(Compiler\) 從初始運算式的型別來推斷變數的型別。  如需詳細資訊，請參閱[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## 指派值  
 您可以使用指派陳述式 \(Assignment Statement\) 執行計算，然後將結果指派給變數，如下列範例所示。  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  這個範例中的等號 \(`=`\) 是一個指派運算子，而不是等號比較運算子。  此值已被指派給 `applesSold` 變數。  
  
 如需詳細資訊，請參閱 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)。  
  
## 變數和屬性  
 跟變數一樣，「*屬性*」\(Property\) 代表您可以存取的值。  然而，它比變數還要來得複雜。  屬性使用程式碼區塊，控制如何設定和擷取值。  如需詳細資訊，請參閱 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)。  
  
## 請參閱  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [為變數進行疑難排解](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)   
 [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)