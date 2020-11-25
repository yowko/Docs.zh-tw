---
title: 重大變更： CA2015：請勿定義衍生自 MemoryManager 之類型的完成項<T>
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2015 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760426"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a>警告 CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T>

預設會啟用 .NET 程式碼分析器規則 [CA2015](/visualstudio/code-quality/ca2015) ，從 .net 5.0 開始。 它會針對衍生自訂完成項的任何類型產生組建警告 <xref:System.Buffers.MemoryManager%601> 。

## <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。 預設會啟用這些規則中的數個，包括 [CA2015](/visualstudio/code-quality/ca2015)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

從定義完成項的衍生自的規則 CA2015 旗標類型 <xref:System.Buffers.MemoryManager%601> 。 將完成項加入至衍生自的型別， <xref:System.Buffers.MemoryManager%601> 可能表示有錯誤。 這表示可能已在中取得的原生資源 <xref:System.Span%601> 正在進行清除，可能是因為仍在使用中 <xref:System.Span%601> 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

- 移除完成項定義。 如需詳細資訊，請參閱 [CA2015](/visualstudio/code-quality/ca2015)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。

## <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
