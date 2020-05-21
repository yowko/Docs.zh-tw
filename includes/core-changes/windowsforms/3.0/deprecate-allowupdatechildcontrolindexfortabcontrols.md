---
ms.openlocfilehash: e1c55eab0b968daab7322350e201b49149e63215
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721748"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>不支援 AllowUpdateChildControlIndexForTabControls 相容性切換

`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`.NET Framework 4.6 和更新版本的 Windows Forms 支援相容性參數，但從 .Net Core 3.0 開始 Windows Forms 不支援。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性參數可讓應用程式在不想要此行為時略過這種重新排列。

在 .NET Core 中， `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 不支援參數。

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
