---
ms.openlocfilehash: 5c1dc42a451d2c6a82e2c2429115db023c610334
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181848"
---
### <a name="switchsystemwindowsformsuselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數

.Net `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` Core 3.0 的 Windows Forms 不支援在 .NET Framework 4.7.2 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.2 開始， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`相容性參數可讓開發人員選擇不使用<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>屬性的新行為，這現在會傳回原始檔控制的參考。 屬性的先前行為是`null`傳回。 如需詳細資訊，請參閱[ \<AppCoNtextSwitchOverrides > 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .net Core 中， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`不支援參數。

#### <a name="version-introduced"></a>引進的版本

3.0 Preview 9

#### <a name="recommended-action"></a>建議的動作

移除參數。 不支援此參數，而且沒有可用的替代功能。

#### <a name="category"></a>分類

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
