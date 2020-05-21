---
ms.openlocfilehash: 97e38685777c7c418c0ccd91f4c433501ecf3aaa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721321"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援 EnableVisualStyleValidation 相容性切換

`Switch.System.Windows.Forms.EnableVisualStyleValidation`.Net Core 3.0 的 Windows Forms 不支援相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。

在 .NET Core 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- 無

<!-- 

#### Affected APIs

- Not detectable via API analysis

-->
