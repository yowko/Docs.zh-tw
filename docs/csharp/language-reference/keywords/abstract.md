---
title: "abstract (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "abstract"
  - "abstract_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "abstract 關鍵字 [C#]"
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# abstract (C# 參考)
`abstract` 修飾詞表示要修飾的項目遺失或實作不完整。  abstract  修飾詞可用於類別、方法、屬性、索引子 \(Indexer\) 和事件。  在類別宣告裡使用 `abstract` 修飾詞，表示該類別只是當做其他類別的基底類別而已。  成員如果標記為抽象，或是包含在抽象類別 \(Abstract Class\) 內，則必須由衍生自此抽象類別的類別實作這個成員。  
  
## 範例  
 在這個範例中，`Square` 類別必須提供 `Area` 的實作，因為它衍生自 `ShapesClass`：  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 抽象類別有下列功能：  
  
-   抽象類別不能執行個體化。  
  
-   抽象類別可能會包含抽象方法和存取子。  
  
-   無法使用 [密封](../../../csharp/language-reference/keywords/sealed.md) 修飾詞來修改抽象類別，因為這兩個修飾詞意義剛好相反。  `sealed` 修飾詞可以不讓類別被繼承，而 `abstract` 修飾詞卻需要類別被繼承。  
  
-   衍生自抽象類別的非抽象類別必須包含所有繼承抽象方法和存取子的實作。  
  
 在方法或屬性宣告裡使用 `abstract` 修飾詞，表示該此方法或屬性沒有包含實作。  
  
 抽象方法有下列特點：  
  
-   抽象方法隱含是一個虛擬方法。  
  
-   抽象方法宣告只允許在抽象類別裡。  
  
-   因為抽象方法宣告沒有提供實際的實作，因此並沒有方法主體，方法宣告僅以分號做為結束而且簽章 \(Signature\) 之後沒有大括號 \({ }\)。  例如：  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     其實作由非抽象類別的成員覆寫方法 [override](../../../csharp/language-reference/keywords/override.md)提供。  
  
-   在抽象方法宣告中使用 [static](../../../csharp/language-reference/keywords/static.md) 或 [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾詞是錯誤的。  
  
 除了宣告和引動過程語法的差異之外，抽象屬性的行為就像抽象方法一樣。  
  
-   在靜態屬性上使用 `abstract` 修飾詞是錯誤的。  
  
-   可在衍生類別中覆寫抽象繼承屬性，方式是包含使用 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞的屬性宣告。  
  
 如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
 抽象類別必須提供所有介面成員的實作。  
  
 實作介面的抽象類別可能將介面方法對應到抽象方法。  例如：  
  
 [!code-cs[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## 範例  
 在這個範例裡，類別 `DerivedClass` 衍生自抽象類別 `BaseClass`。  此抽象類別含有一個抽象方法 \(`AbstractMethod`\) 及兩個抽象屬性 \(`X` 和 `Y`\)。  
  
 [!code-cs[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 上述範例裡，如果您嘗試使用這樣的陳述式來執行抽象類別的個體化：  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 將會取得錯誤訊息，表示編譯器無法建立抽象類別 'BaseClass' 的執行個體。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [虛擬](../../../csharp/language-reference/keywords/virtual.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)