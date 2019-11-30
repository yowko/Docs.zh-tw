---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568107"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute 已移至另一個元件

已移動 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 類別。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和舊版中，<xref:System.ComponentModel.TypeDescriptionProviderAttribute> 類別可在*system.workflow.componentmodel.activity. TypeConverter*元件中找到。

從 .NET Core 3.0 開始，它會在*system.collections.objectmodel.observablecollection*元件中找到。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更只會影響使用反映的應用程式，藉由呼叫方法（例如 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>）或假設該類型在特定元件中的 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 多載，來載入 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 類型。 如果是這種情況，則應該更新方法呼叫中所參考的元件，以反映類型的新元件位置。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- None

<!--

### Affected APIs

- Not detectable via API analysis

-->
