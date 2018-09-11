---
title: 非同步程式設計模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44249032"
---
# <a name="asynchronous-programming-patterns"></a>非同步程式設計模式

.NET Framework 提供三種模式來執行非同步作業：  
  
- **非同步程式設計模型 (APM)** 模式 (也稱為 <xref:System.IAsyncResult> 模式)，其中非同步作業需要 `Begin` 和 `End` 方法 (例如，適用於非同步寫入作業的 `BeginWrite` 和 `EndWrite`)。 在新的程式開發時，不建議使用此模式。 如需詳細資訊，請參閱[非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)。  
  
- **事件架構非同步模式 (EAP)**，需要具有 `Async` 尾碼的方法，並且要求一或多個事件、事件處理常式的委派類型，以及 `EventArg` 衍生類型。 在 .NET Framework 2.0 中採用了 EAP。 在新的程式開發時，不建議使用它。 如需詳細資訊，請參閱[事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。  
  
- **工作架構非同步模式 (TAP)**，使用單一方法來代表非同步作業的起始與完成。 在 .NET Framework 4 中使用了 TAP，且此為在 .NET Framework 中進行非同步程式設計時的建議方法。 C# 中的 [async](~/docs/csharp/language-reference/keywords/async.md) 和 [await](~/docs/csharp/language-reference/keywords/await.md) 關鍵字，以及 Visual Basic 語言中的 [Async](~/docs/visual-basic/language-reference/modifiers/async.md) 和 [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) 運算子，新增 TAP 的語言支援。 如需詳細資訊，請參閱[以工作為基礎的非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
  
## <a name="comparing-patterns"></a>比較模式  

若要快速比較三個模式如何建立非同步作業的模型，請考慮 `Read` 方法，它會將指定的資料量讀取到所提供的緩衝區，並且在指定的位移處開始：  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
此方法的 APM 對應項會公開 `BeginRead` 和 `EndRead` 方法：  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
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
  
TAP 對應項會公開下列單一 `ReadAsync` 方法：  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
如需 TAP、APM 和 EAP 的完整討論，請參閱下節中所提供的連結。  
  
## <a name="related-topics"></a>相關主題

| 標題 | 描述 |
| ----- | ----------- |
| [非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | 描述使用 <xref:System.IAsyncResult> 介面以提供非同步行為的傳統模型。 在新的程式開發時，不建議使用此模型。 |
| [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | 描述提供非同步行為的事件架構舊版模型。 在新的程式開發時，不建議使用此模型。 |
| [工作式非同步模式 (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | 說明新的非同步模式，其根據 <xref:System.Threading.Tasks> 命名空間。 這個模型是在 .NET Framework 4 和更新版本中進行非同步程式設計的建議方法。 |

## <a name="see-also"></a>另請參閱

- [C# 中的非同步程式設計](~/docs/csharp/async.md)   
- [F# 中的非同步程式設計](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [使用 Async 和 Await 進行非同步程式設計 (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
