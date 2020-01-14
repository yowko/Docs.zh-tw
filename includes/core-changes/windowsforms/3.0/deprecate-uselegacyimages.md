---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937047"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>不支援 UseLegacyImages 相容性切換

.NET Core 3.0 上的 Windows Forms 不支援 .NET Framework 4.8 中引進的 `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.8 開始，`Switch.System.Windows.Forms.UseLegacyImages` 相容性參數會解決在高 DPI 環境中 ClickOnce 案例中可能的影像縮放問題。 當設定為 [`true`] 時，參數可讓使用者在縮放設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。 如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.UseLegacyImages` 參數。

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
