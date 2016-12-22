---
title: "成員 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 類型成員"
  - "類型 [C#], 巢狀類型"
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 成員 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

類別和結構具有代表資料與行為的成員。  類別的成員包括類別中宣告的所有成員，以及其繼承階層中所有類別內的所有成員 \(但不包括建構函式和解構函式\)。  衍生類別 \(Derived Class\) 可以繼承基底類別 \(Base Class\) 中的 Private 成員，但無法加以存取。  
  
 下表列出類別或結構可能包含的成員類型：  
  
|成員|描述|  
|--------|--------|  
|[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)|欄位是在類別範圍 \(Class Scope\) 宣告的變數。  欄位可以是內建的數字型別 \(Numeric Type\) 或其他類別的執行個體 \(Instance\)。  例如，日曆類別可能會有包含目前日期的欄位。|  
|[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)|常數是欄位或屬性，其值是在編譯期間設定且無法變更。|  
|[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)|屬性是類別的方法，會當做類別的欄位進行存取。  屬性可以保護類別欄位，而不會在物件不知情的狀況下變更。|  
|[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)|方法會定義類別可以執行的行動。  方法可以使用提供輸入資料的參數，並可透過參數傳回輸出資料。  方法也可以不使用參數，而直接傳回值。|  
|[事件](../../../csharp/programming-guide/events/index.md)|事件會通知其他物件有關發生的動作，例如按鈕的按下動作或方法成功完成。  事件可使用委派來定義與觸發。|  
|[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|多載運算子 \(Overload Operator\) 被視為是類別成員。  當您多載運算子時，會將其定義為類別中的公用靜態方法。  預先定義的運算子 \(`+`、`*`、`<` 等\) 不視為成員。  如需詳細資訊，請參閱[多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)。|  
|[索引子](../../../visual-basic/reference/command-line-compiler/index.md)|索引子可讓物件以類似於陣列的方式進行索引。|  
|[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)|建構函式是在物件初次建立時所呼叫的方法，  通常是用來初始化物件的資料。|  
|[解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)|解構函式在 C\# 中很少用到。  解構函式是在即將從記憶體移除物件時，由 Runtime Execution Engine 所呼叫的方法。  它們通常是用來確認必須釋放的任何資源都已適當的處理。|  
|[巢狀類型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|巢狀型別是在其他型別中宣告的型別。  巢狀型別通常用來描述只有包含型別會使用的物件。|  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別](../../../standard/base-types/classes.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)   
 [索引子](../../../visual-basic/reference/command-line-compiler/index.md)   
 [事件](../../../csharp/programming-guide/events/index.md)   
 [巢狀類型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)   
 [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)