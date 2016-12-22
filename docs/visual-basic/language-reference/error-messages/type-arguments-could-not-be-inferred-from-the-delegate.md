---
title: "Type arguments could not be inferred from the delegate | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36564"
  - "vbc36564"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36564"
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type arguments could not be inferred from the delegate
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指派陳述式 \(Assignment Statement\) 使用 `AddressOf` 將泛型程序的位址指派給委派，但不會對泛型程序提供任何型別參數。  
  
 通常當您叫用 \(Invoke\) 泛型型別時，會對泛型型別定義的每個型別參數提供型別引數。  如果沒有提供任何型別引數，編譯器會嘗試推斷要傳遞至型別參數的型別。  如果內容沒有提供足夠的資訊讓編譯器推斷型別，就會產生錯誤。  
  
 **錯誤 ID**：BC36564  
  
### 若要更正這個錯誤  
  
-   在 `AddressOf` 運算式中，指定泛型程序的型別引數。  
  
## 請參閱  
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Generic Procedures in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)