---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644016"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數

在 .NET Framework 4.7.2 中引進的 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數，在 .NET Core 3.0 的 Windows Forms 中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.2 開始，`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數可讓開發人員選擇不使用 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性的新行為，這現在會傳回原始檔控制的參考。 先前的屬性行為是傳回 `null`。 如需詳細資訊，請參閱[\<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET Core 中，不支援 `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>Category

Windows 表單

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
