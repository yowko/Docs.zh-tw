---
ms.openlocfilehash: 84b6bfc32f5a73597b227098e5aee1e3450cf85b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198373"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援 EnableVisualStyleValidation 相容性參數

.NET Core 3.0 的 Windows Forms 不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中，`Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.EnableVisualStyleValidation` 參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>Category

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
