---
ms.openlocfilehash: 7a2617f27dfd6bb527ff6d408fae6382075f24ae
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721169"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a>TypeDescriptionProviderAttribute 已移至另一個元件

已 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 移動類別。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和更早版本中， <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 類別位於*system.workflow.componentmodel.activity*中。

從 .NET Core 3.0 開始，它會在*system.collections.objectmodel.observablecollection*元件中找到。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更只會影響使用反映的應用程式，藉 <xref:System.ComponentModel.TypeDescriptionProviderAttribute> 由呼叫方法（例如）或的多載（ <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 假設該類型是在特定元件中）來載入類型。 如果是這種情況，則應該更新方法呼叫中所參考的元件，以反映類型的新元件位置。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

#### Affected APIs

- Not detectable via API analysis

-->
