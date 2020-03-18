---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937047"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>不支援使用傳統圖像相容性開關

.NET 框架 4.8 中引入的`Switch.System.Windows.Forms.UseLegacyImages`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET 框架 4.8`Switch.System.Windows.Forms.UseLegacyImages`開始，相容性開關解決了高 DPI 環境中 ClickOnce 方案中可能存在的圖像縮放問題。 `true`設置為 時，交換器允許使用者在高 DPI 顯示器上恢復舊圖像縮放，其比例設置為大於 100%。 有關詳細資訊，請參閱 GitHub 上的[.NET 框架 4.8 版本資訊](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)。

在 .NET 內核`Switch.System.Windows.Forms.UseLegacyImages`中，不支援交換器。

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
