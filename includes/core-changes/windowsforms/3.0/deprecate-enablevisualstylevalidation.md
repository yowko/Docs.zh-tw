---
ms.openlocfilehash: 196a26bd235e5e2556baa7fac979b3316ff81e1f
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556141"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援 EnableVisualStyleValidation 相容性切換

在 `Switch.System.Windows.Forms.EnableVisualStyleValidation` .Net Core 或 .net 5.0 和更新版本的 Windows Forms 中不支援相容性參數。

#### <a name="change-description"></a>變更描述

在 .NET Framework 中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 相容性參數允許應用程式選擇不驗證數值格式所提供的視覺化樣式。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.EnableVisualStyleValidation` 不支援此參數。

#### <a name="version-introduced"></a>引進的版本

3.0

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
