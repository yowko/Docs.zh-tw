---
title: 重大變更：如果實例已存在，則 CreateCounterSetInstance 會擲回 InvalidOperationException
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 CreateCounterSetInstance 會擲回不同的例外狀況（如果計數器已經存在的話）。
ms.date: 11/01/2020
ms.openlocfilehash: 28042690b71f9b86e4e54748ec75467bbe232684
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760723"
---
# <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a>如果實例已經存在，則 CreateCounterSetInstance 現在會擲回 InvalidOperationException

從 .NET 5.0 開始， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> <xref:System.InvalidOperationException> <xref:System.ArgumentException> 如果計數器集合已經存在，則會擲回，而不是。

## <a name="change-description"></a>變更描述

在 .NET Framework 和 .NET Core 1.0 至3.1，您可以藉由呼叫來建立計數器集合的實例 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 。 但是，如果計數器集合已經存在，則方法會擲回 <xref:System.ArgumentException> 例外狀況。

在 .NET 5.0 和更新版本中，當您呼叫， <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> 且計數器集合存在時， <xref:System.InvalidOperationException> 就會擲回例外狀況。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

如果您在 <xref:System.ArgumentException> 呼叫時捕捉到應用程式中的例外狀況 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> ，請考慮同時攔截 <xref:System.InvalidOperationException> 例外狀況。

> [!NOTE]
> <xref:System.ArgumentException>不建議攔截例外狀況。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
