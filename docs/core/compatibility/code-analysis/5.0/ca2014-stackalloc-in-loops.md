---
title: 重大變更： CA2014：不要在迴圈中使用 stackalloc
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2014 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760427"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a>警告 CA2014：不要在迴圈中使用 stackalloc

預設會啟用 .NET 程式碼分析器規則 [CA2014](/visualstudio/code-quality/ca2014) ，從 .net 5.0 開始。 它會針對在迴圈內使用 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 運算式的任何 c # 程式碼產生組建警告。

## <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。 預設會啟用這些規則中的數個，包括 [CA2014](/visualstudio/code-quality/ca2014)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

規則 CA2014 會尋找在迴圈內使用 [stackalloc 運算式](../../../../csharp/language-reference/operators/stackalloc.md) 的 c # 程式碼。 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 會從目前的堆疊框架配置記憶體。 在目前的方法呼叫傳回之前，不會釋放記憶體，這可能會導致堆疊溢位。 由於您無法攔截堆疊溢位例外狀況，因此應用程式會在發生堆疊溢位時終止。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 避免在迴圈內使用 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 。 在迴圈之外配置記憶體區塊，並在迴圈內重複使用它。 如需詳細資訊，請參閱 [CA2014](/visualstudio/code-quality/ca2014)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。

## <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
