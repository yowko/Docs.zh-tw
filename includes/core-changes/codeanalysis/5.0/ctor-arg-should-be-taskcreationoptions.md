---
ms.openlocfilehash: 6bb3b11ef4e4cb6f6a039c97911b0acca862fe6f
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465563"
---
### <a name="ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a>CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值

預設會啟用 .NET 程式碼分析器規則 [CA2247](/visualstudio/code-quality/ca2247) ，從 .net 5.0 開始。 它會針對傳遞型別引數的函式呼叫產生組建警告 <xref:System.Threading.Tasks.TaskCompletionSource%601> <xref:System.Threading.Tasks.TaskContinuationOptions> 。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 [CA2247](/visualstudio/code-quality/ca2247)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

規則 CA2247 <xref:System.Threading.Tasks.TaskCompletionSource%601> 會尋找傳遞型別引數之函式的呼叫 <xref:System.Threading.Tasks.TaskContinuationOptions> 。 <xref:System.Threading.Tasks.TaskCompletionSource%601>型別具有接受值的函式 <xref:System.Threading.Tasks.TaskCreationOptions> ，以及接受的另一個函式 <xref:System.Object> 。 如果您不小心傳遞 <xref:System.Threading.Tasks.TaskContinuationOptions> 值而非 <xref:System.Threading.Tasks.TaskCreationOptions> 值，則 <xref:System.Object> 會在執行時間呼叫具有參數的函式。 您的程式碼會編譯並執行，但不會有預期的行為。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

- <xref:System.Threading.Tasks.TaskContinuationOptions>以對應的值取代自 <xref:System.Threading.Tasks.TaskCreationOptions> 變數。 請勿隱藏此警告，因為它幾乎一律會在您的程式碼中反白顯示錯誤。 如需詳細資訊，請參閱 [CA2247](/visualstudio/code-quality/ca2247)。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>類別

程式碼分析

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

#### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

-->
