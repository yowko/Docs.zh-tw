---
ms.openlocfilehash: 75baa4f23eae838defafd3ce9b3907a187982a18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937049"
---
### <a name="enablevisualstylevalidation-compatibility-switch-not-supported"></a>不支援啟用視覺化樣式驗證相容性開關

.NET `Switch.System.Windows.Forms.EnableVisualStyleValidation` Core 3.0 上的 Windows 表單不支援相容性開關。

#### <a name="change-description"></a>變更描述

在 .NET 框架`Switch.System.Windows.Forms.EnableVisualStyleValidation`中，相容性開關允許應用程式選擇不驗證以數位形式提供的可視樣式。

在 .NET 內核`Switch.System.Windows.Forms.EnableVisualStyleValidation`中，不支援交換器。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- None

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
