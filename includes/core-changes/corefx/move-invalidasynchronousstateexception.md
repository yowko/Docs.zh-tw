---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217098"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>System.componentmodel.invalidasynchronousstateexception 已移至另一個元件

已<xref:System.ComponentModel.InvalidAsynchronousStateException>移動類別。

#### <a name="change-description"></a>變更描述

在 .net Core 2.2 和更早版本中<xref:System.ComponentModel.InvalidAsynchronousStateException> ，類別位於*system.workflow.componentmodel.activity*中。

從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更只會影響使用反映的應用程式<xref:System.ComponentModel.InvalidAsynchronousStateException>來載入，其方式是<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>呼叫方法（例如<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ）或的多載，其假設該類型是在特定元件中。 如果是這種情況，則應該更新方法呼叫中所參考元件的元件，以反映類型的新元件位置。

#### <a name="category"></a>分類

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
