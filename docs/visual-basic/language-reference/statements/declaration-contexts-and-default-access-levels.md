---
title: "Declaration Contexts and Default Access Levels (Visual Basic) | Microsoft Docs"
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
  - "module level, defined"
  - "declaration contexts, Visual Basic"
  - "procedure level, defined"
  - "namespace level, defined"
  - "access levels, Visual Basic"
  - "access levels, default levels"
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declaration Contexts and Default Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個主題會說明可與其他型別一起宣告的 Visual Basic 型別，若未指定，則說明其存取層級預設值為何。  
  
## 宣告內容層級  
 程式設計項目的「*宣告內容*」\(Declaration Context\) 是它被宣告的程式碼區域。  這通常是另一個程式設計項目，之後稱為「*含有項目*」。  
  
 以下是宣告內容的層級：  
  
-   *命名空間層級*：位於原始程式檔或命名空間，但不在類別、結構、模組或介面中  
  
-   *模組層級*：位於類別、結構、模組或介面，但不在程序或區塊中  
  
-   *程序層級*：位於程序或區塊中 \(例如 `If` 或 `For`\)  
  
 下表會針對各種宣告的程式設計項目，根據其宣告內容來顯示其預設存取層級。  
  
|宣告項目|命名空間層級|模組層級|程序層級|  
|----------|------------|----------|----------|  
|變數 \([Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)\)|不允許。|`Private` \(`Public` 在 `Structure` 中，不能在 `Interface` 中\)|`Public`|  
|常數 \([Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)\)|不允許。|`Private` \(`Public` 在 `Structure` 中，不能在 `Interface` 中\)|`Public`|  
|列舉型別 \([Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)\)|`Friend`|`Public`|不允許。|  
|類別 \([Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)\)|`Friend`|`Public`|不允許。|  
|結構 \([Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)\)|`Friend`|`Public`|不允許。|  
|模組 \([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)\)|`Friend`|不允許。|不允許。|  
|介面 \([Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)\)|`Friend`|`Public`|不允許。|  
|程序 \([Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)、[Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)\)|不允許。|`Public`|不允許。|  
|外部參照 \([Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)\)|不允許。|`Public` \(`Interface` 中不允許\)|不允許。|  
|運算子 \([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)\)|不允許。|`Public` \(不能在 `Interface` 或 `Module` 中\)|不允許。|  
|屬性 \([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)\)|不允許。|`Public`|不允許。|  
|預設屬性 \([Default](../../../visual-basic/language-reference/modifiers/default.md)\)|不允許。|`Public` \(`Module` 中不允許\)|不允許。|  
|事件 \([Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)\)|不允許。|`Public`|不允許。|  
|委派 \([Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)\)|`Friend`|`Public`|不允許。|  
  
 如需詳細資訊，請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## 請參閱  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)