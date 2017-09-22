---
title: "lock 陳述式 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00dcbb9feec11587265bf61667d91c2c1598065b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="lock-statement-c-reference"></a>lock 陳述式 (C# 參考)
`lock` 關鍵字可藉由取得指定物件的互斥鎖定、執行陳述式，然後釋放鎖定，以將陳述式區塊標示為關鍵區段。 下列範例包括 `lock` 陳述式。  
  
```csharp  
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
  
 如需詳細資訊，請參閱[執行緒同步處理](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)。  
  
## <a name="remarks"></a>備註  
 `lock` 關鍵字可確保當關鍵區段中已有執行緒時，另一個執行緒不會進入程式碼的關鍵區段。 如果另一個執行緒嘗試進入鎖定的程式碼，它將會等候、封鎖，直到釋放物件。  
  
 [執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)一節說明執行緒的相關資訊。  
  
 `lock` 關鍵字會在區塊開頭呼叫 <xref:System.Threading.Monitor.Enter%2A>，在區塊結尾呼叫 <xref:System.Threading.Monitor.Exit%2A>。 如果 <xref:System.Threading.Thread.Interrupt%2A> 插斷的執行緒正在等候進入 `lock` 陳述式，便會擲回 <xref:System.Threading.ThreadInterruptedException>。  
  
 一般情況下，請避免鎖定 `public` 類型，或超出程式碼控制範圍的執行個體。 `lock (this)`、`lock (typeof (MyType))` 和 `lock ("myLock")` 等常見的建構函式則違反這項指導方針：  
  
-   如果可以公開存取執行個體的話，`lock (this)` 會成為問題。  
  
-   如果可以公開存取 `MyType` 的話，`lock (typeof (MyType))` 會成為問題。  
  
-   由於處理序中使用相同字串的任何其他程式碼，將會共用相同的鎖定，因此 `lock("myLock")` 會成為問題。  
  
 最佳做法是定義要鎖定的 `private` 物件或 `private static` 物件變數，以保護通用於所有執行個體的資料。  
  
 您不能在 `lock` 陳述式主體中使用 [await](../../../csharp/language-reference/keywords/await.md) 關鍵字。  
  
## <a name="example"></a>範例  
 下列範例會示範執行緒的簡易使用方式，而不在 C# 中使用鎖定。  
  
 [!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例會使用執行緒和 `lock`。 只要 `lock` 陳述式存在，則該陳述式區塊就是關鍵區段，且 `balance` 永遠不會是負數。  
  
 [!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Reflection.MethodImplAttributes>   
 <xref:System.Threading.Mutex>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)   
 @System.Threading.Monitor   
 [Interlocked 作業](http://msdn.microsoft.com/library/cbda7114-c752-4f3e-ada1-b1e8dd262f2b)   
 [AutoResetEvent](http://msdn.microsoft.com/library/6d39c48d-6b37-4a9b-8631-f2924cfd9c18)   
 [執行緒同步處理](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)
