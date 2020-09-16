---
title: 程式碼分析的重大變更
description: 列出 .NET 來源程式碼分析器中的重大變更。
ms.date: 09/02/2020
ms.openlocfilehash: 3cbe2ecf5d08084db542db0c2da016f1f391452e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538915"
---
# <a name="code-analysis-breaking-changes"></a>程式碼分析的重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [CA1416：平臺相容性](#ca1416-platform-compatibility) | 5.0 |
| [CA1417： P/Invoke 的字串參數上的 OutAttribute](#ca1417-outattribute-on-string-parameter-for-pinvoke) | 5.0 |
| [CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | 5.0 |
| [CA2013：請勿使用具有值類型的 ReferenceEquals](#ca2013-do-not-use-referenceequals-with-value-types) | 5.0 |
| [CA2014：請勿在迴圈中使用 stackalloc](#ca2014-do-not-use-stackalloc-in-loops) | 5.0 |
| [CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | 5.0 |
| [CA2200:必須重新擲回以保存堆疊詳細資料](#ca2200-rethrow-to-preserve-stack-details) | 5.0 |
| [CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | 5.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ca2200-rethrow-to-preserve-stack-details](../../../includes/core-changes/codeanalysis/5.0/ca2200-rethrow-to-preserve-stack-details.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
