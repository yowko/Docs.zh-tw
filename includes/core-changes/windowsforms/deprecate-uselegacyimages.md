---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181826"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>不支援 UseLegacyImages 相容性參數

.Net `Switch.System.Windows.Forms.UseLegacyImages` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.8 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.8 開始， `Switch.System.Windows.Forms.UseLegacyImages`相容性交換器在高 DPI 環境中解決 ClickOnce 案例中可能的影像縮放問題。 設定為`true`時，參數可讓使用者在其小數值設定為大於 100% 的高 DPI 顯示器上還原舊版影像縮放比例。 如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。

在 .net Core 中， `Switch.System.Windows.Forms.UseLegacyImages`不支援參數。

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
