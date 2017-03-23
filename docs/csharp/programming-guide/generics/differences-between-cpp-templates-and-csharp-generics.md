---
title: "C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "泛型 [C#], 與 C++ 樣板的比較"
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# C++ 樣板和 C# 泛型之間的差異 (C# 程式設計手冊)
C\# 泛型和 C\+\+ 樣板都是支援參數型型別的語言功能。  然而，兩者還是有許多不同之處。  就語法而言，C\# 泛型對參數型型別較為簡單，沒有 C\+\+ 樣板的複雜性。  此外，C\# 也不打算提供 C\+\+ 樣板具備的所有功能。  以實作來說，兩者主要的不同是，C\# 泛型型別替換是在執行階段進行，因此會為執行個體化的物件保留泛型型別資訊。  如需詳細資訊，請參閱 [執行階段中的泛型](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)。  
  
 以下是 C\# 泛型和 C\+\+ 樣板的主要不同點：  
  
-   C\# 泛型提供的彈性不如 C\+\+ 樣板。  例如，您無法在 C\# 泛型類別中呼叫算術運算子，不過可以呼叫使用者定義的運算子。  
  
-   C\# 不允許非型別樣板參數，例如 `template C<int i> {}`。  
  
-   C\# 不支援明確特製化，意即自訂特定型別的樣板實作。  
  
-   C\# 不支援部分特製化，意即自訂型別引數子集的實作。  
  
-   C\# 不允許將型別參數當做泛型型別的基底類別使用。  
  
-   C\# 不允許型別參數有預設型別。  
  
-   在 C\# 中，泛型型別參數本身不能為泛型，但建構的型別可以當做泛型使用。  C\+\+ 允許樣板參數。  
  
-   C\+\+ 允許樣板中有並非對所有型別參數都有效的程式碼，稍後並會檢查樣板中是否有當做型別參數使用的特定型別。  C\# 規定類別中所撰寫的程式碼必須能夠配合任何符合條件約束的型別使用。  例如，在 C\+\+ 中，您可以撰寫函式，將算術運算子 `+` 和 `-` 用於型別參數的物件上，但若使用的型別不支援這些運算子，樣板具現化時就會產生錯誤。  C\# 不允許這個情形，唯一允許的程式語言建構，是可以從條件約束推算的語言建構。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [樣板](/visual-cpp/cpp/templates-cpp)