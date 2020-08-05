---
ms.openlocfilehash: d69f619522c7abc3171f1c089e53cc2754899f93
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556142"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>不支援 UseLegacyImages 相容性切換

`Switch.System.Windows.Forms.UseLegacyImages`.Net Core 或 .net 5.0 及更新版本的 Windows Forms 不支援在 .NET Framework 4.8 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.8 開始， `Switch.System.Windows.Forms.UseLegacyImages` 相容性參數在高 DPI 環境的 ClickOnce 案例中解決可能的影像縮放問題。 設定為時 `true` ，參數可讓使用者在其小數值設定為大於100% 的高 DPI 顯示器上還原舊版影像縮放比例。 如需詳細資訊，請參閱 GitHub 上的[.NET Framework 4.8 版本](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)資訊。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.UseLegacyImages` 不支援此參數。

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
