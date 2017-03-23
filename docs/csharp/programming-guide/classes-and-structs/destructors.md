---
title: "解構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "~ [C#], 解構函式中"
  - "C# 語言, 解構函式"
  - "解構函式 [C#]"
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# 解構函式 (C# 程式設計手冊)
解構函式是用來解構類別的執行個體。  
  
## 備註  
  
-   結構中無法定義解構函式。  它們只能與類別一起使用。  
  
-   一個類別只能有一個解構函式。  
  
-   解構函式不能被繼承或多載。  
  
-   解構函式不能被呼叫。  它們會被自動叫用。  
  
-   解構函式不使用修飾詞或參數。  
  
 例如，下列是 `Car` 類別之解構函式的宣告：  
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  
  
 解構函式會隱含呼叫物件之基底類別 \(Base Class\) 上的 <xref:System.Object.Finalize%2A>。  因此，前述的解構函式程式碼會隱含地轉譯為下列程式碼：  
  
```  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 這表示繼承鏈結中的所有執行個體都會遞迴地呼叫 `Finalize` 方法 \(從最具衍生性的到最低衍生性的\)。  
  
> [!NOTE]
>  您不應使用空的解構函式。  當類別包含解構函式時，便會在 `Finalize` 佇列中建立一個項目。  當呼叫解構函式時，即會叫用記憶體回收行程處理佇列。  如果解構函式是空的，則只會導致不必要的效能損失。  
  
 程式設計人員無法控制呼叫解構函式的時間，因為這是由記憶體回收行程所決定的。  記憶體回收行程會檢查不再被應用程式使用的物件。  如果它將物件視為符合解構資格，便會呼叫解構函式 \(如果存在\)，並且回收用來儲存該物件的記憶體。  當程式結束時，解構函式也會被呼叫。  
  
 呼叫 <xref:System.GC.Collect%2A> 即可強制記憶體回收，但在多數情況下，都應該避免這種情形，因為這樣可能會形成效能問題。  
  
## 使用解構函式來釋放資源  
 一般來說，與透過並未針對執行階段使用記憶體回收的語言進行開發相較之下，C\# 並不需要太多的記憶體管理動作。  這是因為 .NET Framework 記憶體回收行程隱含管理您物件的記憶體配置和釋放。  但是，當您的應用程式封裝 Unmanaged 資源 \(例如視窗、檔案和網路連線\) 時，則您應使用解構函式來釋放這些資源。  當物件符合解構資格時，記憶體回收行程便會執行該物件的 `Finalize` 方法。  
  
## 明確釋放資源  
 如果您的應用程式使用過多的外部資源，我們也建議您在記憶體回收行程釋放該物件之前，提供明確釋放資源的方法。  實作對於物件執行必要清除之 <xref:System.IDisposable> 介面中的 `Dispose` 方法，即可做到這點。  這會顯著提升應用程式的效能。  雖然使用此方法明確控制資源，但是當呼叫 `Dispose` 方法失敗時，解構函式仍將成為清除資源的防護措施。  
  
 如需清除資源的詳細資料，請參閱下列主題：  
  
-   [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)  
  
-   [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)  
  
-   [Using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)  
  
## 範例  
 下列範例建立三個形成繼承鏈結的類別。  `First` 類別是基底類別、`Second` 衍生自 `First`，而 `Third` 衍生自 `Second`。  三個類別都有解構函式。  在 `Main()` 中，會建立衍生最多之類別的執行個體。  當程式執行時，請注意，將會依照從衍生最多的到衍生最少的順序，自動呼叫三個類別的解構函式。  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.IDisposable>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)