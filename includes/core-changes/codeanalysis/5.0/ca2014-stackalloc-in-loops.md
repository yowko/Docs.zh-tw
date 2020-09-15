---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065135"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a>CA2014：請勿在迴圈中使用 stackalloc

預設會啟用 .NET 程式碼分析器規則 [CA2014](/visualstudio/code-quality/ca2014) ，從 .net 5.0 開始。 它會針對在迴圈內使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 運算式的任何 c # 程式碼產生組建警告。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 [CA2014](/visualstudio/code-quality/ca2014)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

規則 CA2014 會尋找在迴圈內使用 [stackalloc 運算式](../../../../docs/csharp/language-reference/operators/stackalloc.md) 的 c # 程式碼。 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 會從目前的堆疊框架配置記憶體。 在目前的方法呼叫傳回之前，不會釋放記憶體，這可能會導致堆疊溢位。 由於您無法攔截堆疊溢位例外狀況，因此應用程式會在發生堆疊溢位時終止。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

- 避免在迴圈內使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 。 在迴圈之外配置記憶體區塊，並在迴圈內重複使用它。 如需詳細資訊，請參閱 [CA2014](/visualstudio/code-quality/ca2014)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>類別

程式碼分析

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
