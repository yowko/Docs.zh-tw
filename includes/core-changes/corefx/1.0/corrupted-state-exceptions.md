---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135618"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>不支援處理損毀狀態例外狀況

不支援在 .NET Core 中處理損毀的進程狀態例外狀況。

#### <a name="change-description"></a>變更描述

先前，managed 程式碼例外狀況處理常式可能會攔截並處理損毀進程狀態的例外狀況，例如，在 c # 中使用[try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md)語句。

從 .NET Core 1.0 開始，managed 程式碼無法處理損毀的進程狀態例外狀況。 通用語言執行時間不會將損毀進程狀態的例外狀況傳遞給 managed 程式碼。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

藉由解決導致問題的情況，避免需要處理損毀進程狀態的例外狀況。 如果絕對需要處理損毀的進程狀態例外狀況，請在 C 或 c + + 程式碼中撰寫例外狀況處理常式。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [legacyCorruptedStateExceptionsPolicy 項目](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
