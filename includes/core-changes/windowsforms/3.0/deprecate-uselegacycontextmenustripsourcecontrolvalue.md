---
ms.openlocfilehash: 3ada05a13ec7acde1d8374ed733d0d51cdfb408c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83720889"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換

`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.Net Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.2 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.2 開始， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數可讓開發人員選擇不使用屬性的新行為 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> ，這現在會傳回原始檔控制的參考。 屬性的先前行為是傳回 `null` 。 如需詳細資訊，請參閱[ \< AppCoNtextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET Core 中， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
