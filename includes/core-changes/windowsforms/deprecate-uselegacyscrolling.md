---
ms.openlocfilehash: 459e7e1f0b5543f069682dadf60668e94b472377
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181757"
---
### <a name="switchsystemwindowsformsdomainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>不支援 DomainUpDown. UseLegacyScrolling 相容性參數

.Net `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.1 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.1 開始， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`相容性切換允許開發人員退出宣告獨立<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>和<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>動作。 此參數會還原舊版行為，其中<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>如果內容文字存在，則會忽略，而開發人員必須在<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>動作之前對<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>控制項使用動作。 如需詳細資訊，請參閱[ \<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .net Core 中， `Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
