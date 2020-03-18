---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147545"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>不正確非同步狀態異常移動到另一個程式集

類<xref:System.ComponentModel.InvalidAsynchronousStateException>已移動。

#### <a name="change-description"></a>變更描述

在 .NET Core 2.2 和<xref:System.ComponentModel.InvalidAsynchronousStateException>早期版本中，類位於*System.元件模型.TypeConverter*程式集中。

從 .NET Core 3.0 開始，它位於*系統.元件模型.原始程式集中*。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="recommended-action"></a>建議的動作

此更改僅影響使用反射來載入 的應用程式<xref:System.ComponentModel.InvalidAsynchronousStateException>，方法是調用 方法，如<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>或 重<xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>載，假定類型位於特定程式集中。 如果是這種情況，則應更新方法調用中引用的程式集以反映類型的新程式集位置。

#### <a name="category"></a>類別

CoreFx

#### <a name="affected-apis"></a>受影響的 API

無。

<!--

### Affected APIs

- Not detectable via API analysis

-->
