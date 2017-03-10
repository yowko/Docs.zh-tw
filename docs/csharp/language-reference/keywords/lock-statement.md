---
title: "lock 陳述式 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "lock_CSharpKeyword"
  - "lock"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lock 關鍵字 [C#]"
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# lock 陳述式 (C# 參考)
`lock` 關鍵字可將陳述式區塊標記為關鍵區段 \(Critical Section\)，其做法是為指定的物件取得互斥鎖定、執行陳述式，接著釋出該鎖定。  下列範例包含一個 `lock` 陳述式。  
  
```  
  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
  
```  
  
 如需詳細資訊，請參閱 [執行緒同步處理](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 備註  
 `lock` 關鍵字可保證有執行緒在關鍵區段時，絕對不會有任何其他執行緒同時也進入這個關鍵區段執行。  如果其他執行緒嘗試進入已鎖定的程式碼，它將會等候、封鎖，直到該物件被釋出。  
  
 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md) 這一章節會討論執行緒的處理。  
  
 `lock` 關鍵字會在區塊開始執行時呼叫 <xref:System.Threading.Monitor.Enter%2A>，並在區塊結束時呼叫 <xref:System.Threading.Monitor.Exit%2A>。  <xref:System.Threading.ThreadInterruptedException> 擲回，如果 <xref:System.Threading.Thread.Interrupt%2A> 中斷等待進入 `lock` 陳述式的執行緒。  
  
 一般而言，請避免鎖定 `public` 型別或程式碼無法控制的執行個體。  有三種常見的建構，分別為 `lock (this)`、`lock (typeof (MyType))` 和 `lock ("myLock")`，違反這項方針：  
  
-   `lock (this)` 在可公開存取執行個體的情況下，會是問題所在。  
  
-   `lock (typeof (MyType))` 在可公開存取 `MyType` 的情況下，會是問題所在。  
  
-   `lock("myLock")` 會是問題所在，因為使用相同字串的處理序中若有任何其他程式碼，將會共用相同的鎖定。  
  
 最佳作法是定義要鎖定的 `private` 物件，或者定義 `private static` 物件變數保護所有執行個體通用的資料。  
  
 您可以在 `lock` 陳述式的主體中不能使用 [等候](../../../csharp/language-reference/keywords/await.md) 關鍵字。  
  
## 範例  
 以下的範例顯示在 C\# 中執行緒 \(但不用鎖定\) 的簡易用法。  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#5)]  
  
## 範例  
 下列範例使用到執行緒與 `lock`。  只要 `lock` 陳述式存在，此陳述式區塊就是關鍵區段，而且 `balance` 永遠不會成為負數。  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/csharp/csrefFixedLock/csrefKeywordsFixedLock.cs#6)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [執行緒](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)   
 [監視器](../Topic/Monitors.md)   
 [Interlocked Operations](../Topic/Interlocked%20Operations.md)   
 [AutoResetEvent](../Topic/AutoResetEvent.md)   
 [執行緒同步處理](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)