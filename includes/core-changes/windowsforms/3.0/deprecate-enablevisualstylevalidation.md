---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937049"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援 EnableVisualStyleValidation 相容性切換

.NET Core 3.0 的 Windows Forms 不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，`Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
