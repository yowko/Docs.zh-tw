---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568153"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>System.componentmodel.invalidasynchronousstateexception 已移至另一個元件

已移動 <xref:System.ComponentModel.InvalidAsynchronousStateException> 類別。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和舊版中，<xref:System.ComponentModel.InvalidAsynchronousStateException> 類別可在*system.workflow.componentmodel.activity. TypeConverter*元件中找到。

從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更只會影響使用反映的應用程式，藉由呼叫方法（例如 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>）或假設該類型在特定元件中的 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 多載，來載入 <xref:System.ComponentModel.InvalidAsynchronousStateException>。 如果是這種情況，則應該更新方法呼叫中所參考元件的元件，以反映類型的新元件位置。

#### <a name="category"></a>Category

CoreFx

#### <a name="affected-apis"></a>受影響的 API

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
