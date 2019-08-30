---
title: 非同步程式設計模式
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36798fabcd42cf7e04b0a6f288736503eecad88b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169117"
---
# <a name="asynchronous-programming-patterns"></a>非同步程式設計模式

.NET 提供三種模式來執行非同步作業：  

- **工作架構非同步模式 (TAP)** ，使用單一方法來代表非同步作業的起始與完成。 TAP 是在 .NET Framework 4 中引進。 **它是在 .NET 中進行非同步程式設計的建議方法。** C# 中的 [async](../../csharp/language-reference/keywords/async.md) 與 [await](../../csharp/language-reference/operators/await.md) 關鍵字，以及 Visual Basic 中的 [Async](../../visual-basic/language-reference/modifiers/async.md) 與 [Await](../../visual-basic/language-reference/operators/await-operator.md) 運算子，都加入對 TAP 的語言支援。 如需詳細資訊，請參閱[以工作為基礎的非同步模式 (TAP)](task-based-asynchronous-pattern-tap.md)  

- **事件架構非同步模式 (EAP)** ，這是用於提供非同步行為的事件架構傳統模型。 它需要一個具有 `Async` 尾碼的方法、一或多個事件，事件處理常式委派類型，以及 `EventArg` 衍生類型。 在 .NET Framework 2.0 中採用了 EAP。 在新的程式開發時，不再建議使用它。 如需詳細資訊，請參閱[事件架構非同步模式 (EAP)](event-based-asynchronous-pattern-eap.md)。  

- **非同步程式設計模型 (APM)** 模式 (亦稱為 <xref:System.IAsyncResult> 模式)，它是使用 <xref:System.IAsyncResult> 介面來提供非同步行為的傳統模型。 在此模式中，同步作業需要 `Begin` 與 `End` 方法 (例如，`BeginWrite` 與 `EndWrite` 來實作非同步寫入作業)。 在新的程式開發時，不建議使用此模式。 如需詳細資訊，請參閱[非同步程式設計模型 (APM)](asynchronous-programming-model-apm.md)。  
  
## <a name="comparison-of-patterns"></a>模式的比較

若要快速比較三個模式如何建立非同步作業的模型，請考慮 `Read` 方法，它會將指定的資料量讀取到所提供的緩衝區，並且在指定的位移處開始：  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

此方法的 TAP 對應項會公開下列單一 `ReadAsync` 方法：  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

EAP 對應項會公開下列類型和成員的集合：  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
APM 對應項會公開 `BeginRead` 與 `EndRead` 方法：  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>另請參閱

- [深入了解非同步](../async-in-depth.md)
- [C# 中的非同步程式設計](../../csharp/async.md)
- [F# 中的非同步程式設計](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
