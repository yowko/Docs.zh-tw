---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538916"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200:必須重新擲回以保存堆疊詳細資料

預設會啟用 .NET 程式碼分析器規則 [CA2200](/visualstudio/code-quality/ca2200) ，從 .net 5.0 開始。 它會針對重新擲回例外狀況的任何區塊產生組建警告 `catch` ，並在語句中明確指定例外狀況 `throw` 。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 [CA2200](/visualstudio/code-quality/ca2200)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

規則 CA2200 會將擲回例外狀況的程式碼加上旗標，並在語句中指定例外狀況變數 `throw` 。 擲回例外狀況時，它所攜帶的部分資訊就是堆疊追蹤。 堆疊追蹤是方法呼叫階層的清單，其開頭為擲回例外狀況的方法，並以捕捉例外狀況的方法結束。 如果在語句中指定例外狀況而重新擲回例外狀況 `throw` ，堆疊追蹤會在目前的方法重新開機，並在擲回例外狀況的原始方法與目前方法遺失之間的方法呼叫清單中重新開機。 若要保留原始堆疊追蹤資訊的例外狀況，請使用 `throw` 語句而不指定例外狀況。

下列程式碼片段不會產生規則 CA2200 的警告。 不過，批註的程式程式碼 *會* 觸發違規。

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

- 重新擲回例外狀況，而不明確指定例外狀況。 如需詳細資訊，請參閱 [CA2200](/visualstudio/code-quality/ca2200)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>類別

程式碼分析

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
