---
ms.openlocfilehash: 7e76c32ddeb50eaf1ee93d7cf3cac7469187cc41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937031"
---
### <a name="allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported"></a>允許更新兒童控制索引ForTab控制相容性開關不支援

.NET 框架 4.6 上的 Windows 表單和更高版本支援`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`相容性開關，但在以 .NET Core 3.0 開頭的 Windows 表單中不支援相容性開關。

#### <a name="change-description"></a>變更描述

在 .NET 框架 4.6 和更高版本中，選擇選項卡重新排序其控制項集合。 相容性`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`開關允許應用程式在這樣做不可取時跳過此重新排序。

在 .NET 內核`Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls`中，不支援交換器。

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
