---
ms.openlocfilehash: ee4a27dde9f1e7756401e3d8b709514082f5d3b1
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556146"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>不支援 DomainUpDown. UseLegacyScrolling 相容性參數

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.Net Core 或 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.1 開始， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 相容性切換允許開發人員退出宣告獨立 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。 此參數會還原舊版行為，其中 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 如果內容文字存在，則會忽略，而開發人員必須在 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作之前對控制項使用動作 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 。 如需詳細資訊，請參閱[ \<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 不支援此參數。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
