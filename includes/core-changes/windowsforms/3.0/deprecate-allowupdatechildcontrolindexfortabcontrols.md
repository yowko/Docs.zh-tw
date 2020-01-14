---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937031"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>不支援 AllowUpdateChildControlIndexForTabControls 相容性切換

.NET Framework 4.6 和更新版本的 Windows Forms 支援 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 相容性參數，但從 .NET Core 3.0 開始 Windows Forms 不支援。

#### <a name="change-description"></a>變更描述

在 .NET Framework 4.6 和更新版本中，選取索引標籤會重新排序其控制項集合。 當此行為不需要時，`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 相容性參數可讓應用程式略過此重新排列。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls` 參數。

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
