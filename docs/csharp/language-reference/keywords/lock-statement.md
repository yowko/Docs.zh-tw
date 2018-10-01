---
title: lock 陳述式 (C# 參考)
description: 使用 C# 鎖定陳述式，將執行緒存取同步至共用資源
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858352"
---
# <a name="lock-statement-c-reference"></a>lock 陳述式 (C# 參考)

`lock` 陳述式可取得所指定物件的互斥鎖定、執行陳述式鎖定，然後釋放鎖定。 持有鎖定時，持有鎖定的執行緒可以再次取得並釋放鎖定。 其他執行緒將無法取得鎖定，並將等待直到釋放鎖定為止。

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

當您將執行緒存取同步至共用資源時，請鎖定專用物件執行個體 (例如 `private readonly object balanceLock = new object();`) 或另一個不太可能由程式碼不相關的部分用作鎖定物件的執行個體。 避免對不同的共用資源使用相同的鎖定物件執行個體，因為其可能導致鎖死或鎖定爭用。 特別是，請避免使用

- `this` (呼叫者可能會將其作為鎖定)、
- <xref:System.Type> 執行個體 (可能會由 [typeof](typeof.md) 運算子或反映取得)、
- 字串執行個體，包括字串常值、

作為鎖定物件。

## <a name="example"></a>範例

下列範例會定義 `Account` 類別，該類別會透過鎖定專用的 `balanceLock` 執行個體來同步對其私用 `balance` 欄位的存取。 使用相同的執行個體進行鎖定，可確保嘗試同時呼叫 `Debit` 或 `Credit` 方法的兩個執行緒無法同時更新 `balance` 欄位。

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# 參考](../index.md)
- [C# 關鍵字](index.md)
- [陳述式關鍵字](statement-keywords.md)
- [Interlocked 作業](../../../standard/threading/interlocked-operations.md)
- [同步處理原始物件概觀](../../../standard/threading/overview-of-synchronization-primitives.md)