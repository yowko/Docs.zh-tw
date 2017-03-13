---
title: "如何：定義抽象屬性 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "抽象屬性 [C#]"
  - "屬性 [C#], abstract"
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# 如何：定義抽象屬性 (C# 程式設計手冊)
下列範例說明如何定義 [abstract](../../../csharp/language-reference/keywords/abstract.md) 屬性。  抽象屬性宣告不會提供屬性存取子的實作，它會宣告類別支援屬性，但存取子實作則會交由衍生類別 \(Derived Class\) 處理。  下列範例示範如何實作繼承自基底類別的抽象屬性。  
  
 這個範例有三個檔案，每個都是單獨編譯，而且所產生的組件會供接下來的編譯參考：  
  
-   abstractshape.cs：包含抽象 `Area` 屬性的 `Shape` 類別。  
  
-   shapes.cs：`Shape` 類別的子類別。  
  
-   shapetest.cs：用以顯示某些 `Shape` 衍生物件區域的測試程式。  
  
 若要編譯此範例，請使用下列命令列：  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 這會建立可執行檔 shapetest.exe。  
  
## 範例  
 這個檔案會宣告 `Shape` 類別，其中包含型別為 `double` 的 `Area` 屬性。  
  
 [!code-cs[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   屬性的修飾詞會置於屬性宣告本身當中。  例如：  
  
    ```  
    public abstract double Area  
    ```  
  
-   宣告抽象屬性時 \(例如，本範例的 `Area`，您只需指出哪些屬性存取子是可用的，但不要實作它們。  在這個範例中，只有 [get](../../../csharp/language-reference/keywords/get.md) 存取子是可用的，所以屬性為唯讀。  
  
## 範例  
 下列程式碼顯示 `Shape` 的三個子類別，以及這些子類別如何覆寫 `Area` 屬性以提供本身的實作。  
  
 [!code-cs[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## 範例  
 下列程式碼會顯示測試程式，用以建立數個 `Shape` 衍生物件並顯示它們的區域。  
  
 [!code-cs[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [如何：使用命令列建立和使用組件](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)