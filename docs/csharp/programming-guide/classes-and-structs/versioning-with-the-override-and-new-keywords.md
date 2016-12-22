---
title: "使用 Override 和 New 關鍵字進行版本控制 (C# 程式設計手冊) | Microsoft Docs"
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
  - "C# 語言, override 和 new"
  - "C# 語言, 版本控制"
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用 Override 和 New 關鍵字進行版本控制 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 語言對於控制不同程式庫的 [base](../../../csharp/language-reference/keywords/base.md) 類別和衍生類別版本，是設計成可以不斷改進，同時也能維持回溯相容性。  舉例來說，這表示 C\# 完全支援在基底 [class](../../../csharp/language-reference/keywords/class.md) 中加入新成員時，其名稱可與衍生類別中的成員相同，而且不會導致未預期的行為。  它同時表示，類別必須明確敘述方法是否要覆寫繼承方法，或者方法是否為隱藏與繼承方法相似名稱的一個新方法。  
  
 在 C\# 中，衍生類別可以包含擁有與基底類別方法相同之名稱的方法。  
  
-   基底類別方法必須定義為 [virtual](../../../csharp/language-reference/keywords/virtual.md)。  
  
-   如果衍生類別中的方法前面沒有加上 [new](../../../csharp/language-reference/keywords/new.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字，編譯器會發出警告，且方法的行為會如同有 `new` 關鍵字一般。  
  
-   如果衍生類別中的方法前面加上 `new` 關鍵字，該方法會定義為與基底類別中的方法無關。  
  
-   如果衍生類別中的方法前面加上 `override` 關鍵字，則衍生類別的物件會呼叫該方法，而不是基底類別方法。  
  
-   衍生類別可使用 `base` 關鍵字呼叫基底類別方法。  
  
-   `override`、`virtual` 和 `new` 關鍵字也可用於屬性、索引子和事件。  
  
 根據預設，C\# 方法是非虛擬的。  如果將方法宣告為虛擬，則任何繼承該方法的類別都可以實作自己的版本。  若要使方法成為虛擬，可以在基底類別的方法宣告中使用 `virtual` 修飾詞。  衍生類別接著便能夠使用 `override` 關鍵字來覆寫基底虛擬方法，或是使用 `new` 關鍵字來隱藏基底類別中的虛擬方法。  如果未指定 `override` 或 `new` 關鍵字，編譯器會發出警告，而且衍生類別中的方法將會隱藏基底類別中的方法。  
  
 以實際情況為例，可以假設 A 公司建立了名為 `GraphicsClass` 的類別以供您的程式使用。  下列是 `GraphicsClass`：  
  
 [!CODE [csProgGuideInheritance#27](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#27)]  
  
 您的公司會使用這個類別，您則用來衍生自己的類別並加入新方法：  
  
 [!CODE [csProgGuideInheritance#28](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#28)]  
  
 您的應用程式使用起來很正常，直到 A 公司發行新版的 `GraphicsClass`，類似下列程式碼：  
  
 [!CODE [csProgGuideInheritance#29](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#29)]  
  
 新版的 `GraphicsClass` 現在包含名為 `DrawRectangle` 的方法。  一開始並不會發生任何問題。  新版本仍然可以與舊版本二進位相容。  您所部署的任何軟體都會繼續執行，就算電腦系統上安裝了新的類別也不會有問題。  目前對方法 `DrawRectangle` 所做的任何呼叫，仍會參考您自己衍生類別中的方法版本。  
  
 不過，一旦您使用新版 `GraphicsClass` 重新編譯應用程式，便會收到編譯器 CS0108 發出的警告。  這個警告會通知您，讓您考量自己的 `DrawRectangle` 方法應如何在應用程式中執行。  
  
 如果您要讓自己的方法覆寫新的基底類別方法，請使用 `override` 關鍵字：  
  
 [!CODE [csProgGuideInheritance#30](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#30)]  
  
 `override` 關鍵字可確保從 `YourDerivedGraphicsClass` 衍生的任何物件都會使用衍生類別版本的 `DrawRectangle`。  不過，從 `YourDerivedGraphicsClass` 衍生的物件仍可使用 base 關鍵字存取基底類別版本的 `DrawRectangle`：  
  
 [!CODE [csProgGuideInheritance#44](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#44)]  
  
 如果您不要讓自己的方法覆寫新的基底類別方法，則適用下列考量：  為避免兩個方法之間的混淆，您可以重新命名方法。  這可能相當耗時間而且容易發生錯誤，在某些情況下並不是實際的做法。  不過，如果您的專案不大，可以使用 Visual Studio 的「重構」選項重新命名方法。  如需詳細資訊，請參閱[Refactoring Classes and Types \(Class Designer\)](/visual-studio/ide/refactoring-classes-and-types-class-designer)。  
  
 此外，您也可以在衍生類別定義中使用關鍵字 `new`，以避免出現警告：  
  
 [!CODE [csProgGuideInheritance#31](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#31)]  
  
 使用 `new` 關鍵字即告知編譯器，您的定義將隱藏基底類別中所包含的定義。  這是預設行為。  
  
## 覆寫和方法選擇  
 如果方法是在類別上指定，而在呼叫時有兩個方法相容時，C\# 編譯器會選擇呼叫最適合的方法，比方有兩個同名的方法，而且參數與傳遞的參數相容時。  例如，下列方法可能會相容：  
  
 [!CODE [csProgGuideInheritance#32](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#32)]  
  
 當在 `Derived` 的執行個體上呼叫 `DoWork` 時，C\# 編譯器會先嘗試呼叫原先在 `Derived` 上宣告的 `DoWork` 版本。  覆寫方法並不是在類別上宣告的，而是基底類別上所宣告方法的新實作。  只有當 C\# 編譯器無法比對方法呼叫與 `Derived` 上的原始方法時，才會嘗試比對呼叫與同名而且參數相容的覆寫方法。  例如：  
  
 [!CODE [csProgGuideInheritance#33](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#33)]  
  
 由於變數 `val` 可隱含轉換成雙精度浮點數，因此 C\# 編譯器會呼叫 `DoWork(double)` 而非 `DoWork(int)`。  避免這情況的方法有兩個。  第一是避免將新方法宣告為與虛擬方法同名。  第二則是指示 C\# 編譯器將 `Derived` 的執行個體轉換成 `Base`，然後藉由搜尋基底類別方法清單的方式呼叫虛擬方法。  由於方法為虛擬，因此會呼叫 `Derived` 上 `DoWork(int)` 的實作。  例如：  
  
 [!CODE [csProgGuideInheritance#34](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideInheritance#34)]  
  
 如需更多的範例`new`和`override`，請參閱[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [繼承](../../../fsharp/language-reference/inheritance.md)