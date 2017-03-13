---
title: "IsFalse Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.isfalse"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AndAlso operator"
  - "IsFalse operator"
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# IsFalse Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

判斷運算式是否為 `False`。  
  
 您無法在程式碼中明確呼叫 `IsFalse`，但 Visual Basic 編譯器 \(Compiler\) 可利用它從 `AndAlso` 子句產生程式碼。  如果定義類別或結構，然後在 `AndAlso` 子句中使用該型別的變數，則必須在該類別或結構上定義 `IsFalse`。  
  
 編譯器會將 `IsFalse` 和 `IsTrue` 運算子視為「*相符的配對*」。  這表示如果定義其中一個，也必須定義另一個。  
  
> [!NOTE]
>  `IsFalse` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列程式碼範例所定義的結構大綱包含 `IsFalse` 和 `IsTrue` 運算子的定義。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## 請參閱  
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)