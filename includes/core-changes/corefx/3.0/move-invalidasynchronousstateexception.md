---
ms.openlocfilehash: 78678b4b352bb063d1521e9aee3492c0cee059b8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720955"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>System.componentmodel.invalidasynchronousstateexception 已移至另一個元件

已 <xref:System.ComponentModel.InvalidAsynchronousStateException> 移動類別。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和更早版本中， <xref:System.ComponentModel.InvalidAsynchronousStateException> 類別位於*system.workflow.componentmodel.activity*中。

從 .NET Core 3.0 開始，它會在*system.workflow.componentmodel.activity*元件中找到。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

這項變更只會影響使用反映的應用程式來載入，其 <xref:System.ComponentModel.InvalidAsynchronousStateException> 方式是呼叫方法（例如）或的多載 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> ，其假設該類型是在特定元件中。 如果是這種情況，請更新方法呼叫中所參考的元件，以反映類型的新元件位置。

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

#### Affected APIs

- Not detectable via API analysis

-->
