---
ms.openlocfilehash: 3db4b0b42a154c5bc9296889ae9dc4b7ecf1e58e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556144"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>不支援 AllowUpdateChildControlIndexForTabControls 相容性切換

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`.NET Framework 4.6 和更新版本的 Windows Forms 支援相容性參數，但 .Net Core 或 .net 5.0 及更新版本不支援此功能。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性參數可讓應用程式在不想要此行為時略過這種重新排列。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 不支援此參數。

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
