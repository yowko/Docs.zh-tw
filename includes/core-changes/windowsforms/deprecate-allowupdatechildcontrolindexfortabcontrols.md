---
ms.openlocfilehash: 1d01de4b978309e05a6036953f2a6909628a2480
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181778"
---
### <a name="switchsystemwindowsformsallowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>不支援 AllowUpdateChildControlIndexForTabControls 相容性參數

.NET Framework `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 4.6 和更新版本的 Windows Forms 支援相容性參數，但從 .net Core 3.0 開始 Windows Forms 不支援。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性參數可讓應用程式在不想要此行為時略過這種重新排列。

在 .net Core 中， `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`不支援參數。

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
