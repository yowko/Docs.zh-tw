---
ms.openlocfilehash: e6bb1d53cbe1883b8faef75bd22942bd4f65a5e6
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181863"
---
### <a name="switchsystemwindowsformsenablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援 EnableVisualStyleValidation 相容性參數

.Net `Switch.System.Windows.Forms.EnableVisualStyleValidation` Core 3.0 的 Windows Forms 不支援相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation`相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。 

在 .net Core 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation`不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
