---
ms.openlocfilehash: dd850e83540ffed4dc95b00f807f49b0dd3725e9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721125"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>不支援 DomainUpDown. UseLegacyScrolling 相容性參數

`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.1 開始， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 相容性切換允許開發人員退出宣告獨立 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 動作。 此參數會還原舊版行為，其中 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 如果內容文字存在，則會忽略，而開發人員必須在 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 動作之前對控制項使用動作 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 。 如需詳細資訊，請參閱[ \< AppCoNtextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET Core 中， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` 不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

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
