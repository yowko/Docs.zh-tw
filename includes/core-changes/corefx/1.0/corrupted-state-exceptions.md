---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031996"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a>不支援處理損毀狀態例外狀況

不支援在 .NET Core 中處理損毀的進程狀態例外狀況。

#### <a name="change-description"></a>變更描述

先前，managed 程式碼例外狀況處理常式可能會攔截並處理損毀進程狀態的例外狀況，例如，使用 c # 中的 [try catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) 語句。

從 .NET Core 1.0 開始，managed 程式碼無法處理損毀進程狀態的例外狀況。 Common language runtime 不會將損毀進程狀態的例外狀況傳遞給 managed 程式碼。

#### <a name="version-introduced"></a>引進的版本

1.0

#### <a name="recommended-action"></a>建議的動作

藉由解決導致這些例外狀況的情況，以避免需要處理損毀進程狀態的例外狀況。 如果絕對必須處理已損毀的進程狀態例外狀況，請在 C 或 c + + 程式碼中撰寫例外狀況處理常式。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [legacyCorruptedStateExceptionsPolicy 項目](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
