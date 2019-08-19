---
title: lock 陳述式 - C# 參考
ms.custom: seodec18
description: 使用 C# lock 陳述式，來同步處理執行緒對共用資源的存取
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 7ae19e48467bf5feca115c993c2299c1ecbaadc7
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566341"
---
# <a name="lock-statement-c-reference"></a>lock 陳述式 (C# 參考)

`lock` 陳述式會取得指定物件的互斥鎖定、執行陳述式區塊，然後釋放鎖定。 持有鎖定時，持有鎖定的執行緒可以再次取得並釋放鎖定。 其他執行緒將無法取得鎖定，並將等待直到釋放鎖定為止。

`lock` 陳述式格式為

```csharp
lock (x)
{
    // Your code...
}
```

`x` 是[參考型別](reference-types.md)的運算式。 其完全等同於

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

由於程式碼會使用 [try...finally](try-finally.md) 區塊，即使在 `lock` 陳述式的主體內擲回例外狀況，也會釋放鎖定。

您不能在 `lock` 陳述式主體中使用 [await](await.md) 關鍵字。

## <a name="remarks"></a>備註

當您同步處理執行緒對共用資源的存取時，請鎖定專用物件執行個體 (例如 `private readonly object balanceLock = new object();`) 或另一個不太可能由程式碼不相關的部分用作鎖定物件的執行個體。 避免對不同的共用資源使用相同的鎖定物件執行個體，因為其可能導致鎖死或鎖定爭用。 尤其要避免使用下列項目當作鎖定物件：

- `this`，呼叫者可能會將其作為鎖定。
- <xref:System.Type> 執行個體，因為這些可能會由 [typeof](../operators/type-testing-and-cast.md#typeof-operator) 運算子或反映取得。
- 字串執行個體 (包括字串常值)，因為那些可能會[暫留](/dotnet/api/system.string.intern#remarks)。

## <a name="example"></a>範例

下列範例會定義 `Account` 類別，該類別會透過鎖定專用的 `balanceLock` 執行個體來同步對其私用 `balance` 欄位的存取。 使用相同的執行個體進行鎖定，可確保嘗試同時呼叫 `Debit` 或 `Credit` 方法的兩個執行緒無法同時更新 `balance` 欄位。

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的 [lock 陳述式](~/_csharplang/spec/statements.md#the-lock-statement)一節。

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [同步處理原始物件概觀](../../../standard/threading/overview-of-synchronization-primitives.md)
