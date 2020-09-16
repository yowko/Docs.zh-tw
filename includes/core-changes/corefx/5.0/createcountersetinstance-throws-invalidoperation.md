---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144473"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException

從 .NET 5.0 開始， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> 如果計數器集合已經存在，則會擲回，而不是。

#### <a name="change-description"></a>變更描述

在 .NET Framework 和 .NET Core 1.0 至3.1，您可以藉由呼叫來建立計數器集合的實例 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 。 但是，如果計數器集合已經存在，則方法會擲回 <xref:System.ArgumentException> 例外狀況。

在 .NET 5.0 和更新版本中，當您呼叫， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 且計數器集合存在時， <xref:System.InvalidOperationException> 就會擲回例外狀況。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 5

#### <a name="recommended-action"></a>建議的動作

如果您在 <xref:System.ArgumentException> 呼叫時捕捉到應用程式中的例外狀況 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ，請考慮同時攔截 <xref:System.InvalidOperationException> 例外狀況。

> [!NOTE]
> <xref:System.ArgumentException>不建議攔截例外狀況。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
