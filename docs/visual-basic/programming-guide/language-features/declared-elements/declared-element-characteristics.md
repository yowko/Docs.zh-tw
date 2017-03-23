---
title: "Declared Element Characteristics (Visual Basic) | Microsoft Docs"
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
  - "declared elements, lifetime"
  - "access levels, declared elements"
  - "declared elements, scope"
  - "visibility, declared elements"
  - "elements, programming"
  - "scope, declared elements"
  - "lifetime, declared elements"
  - "declared elements, access level"
  - "data types [Visual Basic], declared elements"
  - "declared elements, visibility"
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Declared Element Characteristics (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

宣告項目的「*特性*」\(Characteristic\) 應從該項目如何影響程式碼，以及兩者之間互動的角度來觀察。  每個宣告項目都有一個或多個與其關聯的特性，如下：  
  
-   「*資料型別*」\(Data type\) \- 項目可保留的值，以及儲存這些值的方式。  如需詳細資訊，請參閱 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。  
  
-   「*存留期*」\(Lifetime\) \- 可使用該項目的執行時間。  如需詳細資訊，請參閱 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
-   「*範圍*」\(Scope\) \- 不需完整名稱而可參考該項目的整組程式碼。  如需詳細資訊，請參閱 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)。  
  
-   「*存取層級*」\(Access Level\) \- 程式碼對該項目的使用權限。  如需詳細資訊，請參閱 [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)。  
  
## 項目特性  
 下表顯示的是宣告項目及可套用至每一個項目的特性。  
  
|項目|資料型別|存留期|範圍 <sup>1</sup>|存取層級|  
|--------|----------|---------|---------------------|----------|  
|變數|是|是|是|是|  
|常數|是|否|是|是|  
|列舉|是|否|是|是|  
|結構|否|否|是|是|  
|屬性|是|是|是|是|  
|方法|否|是|是|是|  
|程序 \(`Sub` 或 `Function`\)|否|是|是|是|  
|程序參數|是|是|是|否|  
|函式傳回|是|是|是|否|  
|運算子|是|否|是|是|  
|介面|否|否|是|是|  
|類別|否|否|是|是|  
|事件|否|否|是|是|  
|委派|否|否|是|是|  
  
 <sup>1</sup> 範圍有時是指「*可視性*」\(Visibility\)。  
  
## 請參閱  
 [Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)