---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598073"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a>CA2013：請勿使用具有值類型的 ReferenceEquals

預設會啟用 .NET 程式碼分析器規則 [CA2013](/visualstudio/code-quality/ca2013) ，從 .net 5.0 開始。 它會針對 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 用來比較一或多個數值型別是否相等的任何程式碼產生組建警告。

#### <a name="change-description"></a>變更描述

從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。 預設會啟用這些規則中的數個，包括 [CA2013](/visualstudio/code-quality/ca2013)。 如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。

[規則 CA2013] <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 會尋找用來比較一或多個數值型別是否相等的實例。 以這種方式比較相等的數值型別可能會導致不正確的結果，因為這些值會在比較之前先進行過迭。 <xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`即使比較的值代表實值型別的實例，也會傳回。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

- 將程式碼變更為使用適當的等號比較運算子，例如 `==` 。 您不應該隱藏這個警告。

- 若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。 如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。

#### <a name="category"></a>類別

程式碼分析

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->
