---
title: "Derived Math Functions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "arithmetic operations, derived math functions"
  - "cosecant function"
  - "arcsecant function"
  - "arccotangent function"
  - "functions [Visual Basic], derived math functions"
  - "inverse functions"
  - "math functions, derived"
  - "derived math functions"
  - "cotangent function"
  - "angles"
  - "secant function"
  - "trigonometric functions"
  - "logarithms"
  - "arccosecant function"
  - "hyperbolic functions"
  - "arcsine function"
  - "degrees"
  - "arccosine function"
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Derived Math Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

下表顯示非內建的數學函式，這些函式可以衍生自 <xref:System.Math?displayProperty=fullName> 物件的內建數學函式。  將 `Imports System.Math` 加入至檔案或專案，您即可存取內建數學函式。  
  
|Function|衍生的相等函式|  
|--------------|-------------|  
|Secant \(正割\) \(Sec\(x\)\)|1 \/ Cos\(x\)|  
|Cosecant \(餘割\) \(Csc\(x\)\)|1 \/ Sin\(x\)|  
|Cotangent \(餘切\) \(Ctan\(x\)\)|1 \/ Tan\(x\)|  
|Inverse Sine \(反正弦\) \(Asin\(x\)\)|Atan\(x \/ Sqrt\(\-x \* x \+ 1\)\)|  
|Inverse Cosine \(反餘弦\) \(Acos\(x\)\)|Atan\(\-x \/ Sqrt\(\-x \* x \+ 1\)\) \+ 2 \* Atan\(1\)|  
|Inverse Secant \(反正割\) \(Asec\(x\)\)|2 \* Atan\(1\) – Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Inverse Cosecant \(反餘割\) \(Acsc\(x\)\)|Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Inverse Cotangent \(反餘切\) \(Acot\(x\)\)|2 \* Atan\(1\) \- Atan\(x\)|  
|Hyperbolic Sine \(雙曲線正弦\) \(Sinh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ 2|  
|Hyperbolic Cosine \(雙曲線餘弦\) \(Cosh\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ 2|  
|Hyperbolic Tangent \(雙曲線正切\) \(Tanh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Hyperbolic Secant \(雙曲線正割\) \(Sech\(x\)\)|2 \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Hyperbolic Cosecant \(雙曲線餘割\) \(Csch\(x\)\)|2 \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Hyperbolic Cotangent \(雙曲線餘切\) \(Coth\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Inverse Hyperbolic Sine \(反雙曲線正弦\) \(Asinh\(x\)\)|Log\(x \+ Sqrt\(x \* x \+ 1\)\)|  
|Inverse Hyperbolic Cosine \(反雙曲線餘弦\) \(Acosh\(x\)\)|Log\(x \+ Sqrt\(x \* x – 1\)\)|  
|Inverse Hyperbolic Tangent \(反雙曲線正切\) \(Atanh\(x\)\)|Log\(\(1 \+ x\) \/ \(1 – x\)\) \/ 2|  
|Inverse Hyperbolic Secant \(反雙曲線正割\) \(AsecH\(x\)\)|Log\(\(Sqrt\(\-x \* x \+ 1\) \+ 1\) \/ x\)|  
|Inverse Hyperbolic Cosecant \(反雙曲線餘割\) \(Acsch\(x\)\)|Log\(\(Sign\(x\) \* Sqrt\(x \* x \+ 1\) \+ 1\) \/ x\)|  
|Inverse Hyperbolic Cotangent \(反雙曲線餘切\) \(Acoth\(x\)\)|Log\(\(x \+ 1\) \/ \(x – 1\)\) \/ 2|  
  
## 請參閱  
 [數學函式](../../../visual-basic/language-reference/functions/math-functions.md)