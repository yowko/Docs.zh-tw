---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021637"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>不合法的異步狀態異常移至另一個程式集

類<xref:System.ComponentModel.InvalidAsynchronousStateException>已移動。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和<xref:System.ComponentModel.InvalidAsynchronousStateException>早期版本中,類位於*System.元件模型.TypeConverter*程式集中。

從 .NET Core 3.0 開始,它位於*系統.元件模型.原始程式集中*。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

此更改僅影響使用反射來載入 的<xref:System.ComponentModel.InvalidAsynchronousStateException>應用程式 ,方法是調用<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>方法,<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>如或重載,假定類型位於特定程式集中。 如果是這種情況,則應更新方法調用中引用的程式集以反映類型的新程式集位置。

#### <a name="category"></a>類別

核心 .NET 函式庫

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

### Affected APIs

- Not detectable via API analysis

-->
