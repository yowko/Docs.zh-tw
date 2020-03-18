---
ms.openlocfilehash: 80fc75d0736e2ae17699073a025e79b52b340613
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937009"
---
### <a name="domainupdownuselegacyscrolling-compatibility-switch-not-supported"></a>域向上向下.不使用舊卷滾動相容性開關

.NET 框架 4.7.1 中引入的`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET 框架 4.7.1`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`開始，相容性開關允許開發人員退出宣告獨立<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>操作和<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>操作。 交換器還原了舊行為，如果存在上下文文本，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>則忽略 該行為，並且開發人員需要在<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>操作之前對控制項使用操作。 有關詳細資訊，請參閱[\<應用上下文切換覆蓋>元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET 內核`Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling`中，不支援交換器。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.DomainUpDown.DownButton`
- `M:System.Windows.Forms.DomainUpDown.UpButton`

-->
