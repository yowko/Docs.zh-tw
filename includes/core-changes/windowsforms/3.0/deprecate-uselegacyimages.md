---
ms.openlocfilehash: c980b0c0be9f4d6a529baa0743dec9ac16ca0d7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721183"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>不支援 UseLegacyImages 相容性切換

`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.8 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.8 開始， `Switch.System.Windows.Forms.UseLegacyImages` 相容性交換器在高 DPI 環境中解決 ClickOnce 案例中可能的影像縮放問題。 設定為時 `true` ，參數可讓使用者在其小數值設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。 如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。

在 .NET Core 中， `Switch.System.Windows.Forms.UseLegacyImages` 不支援參數。

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
