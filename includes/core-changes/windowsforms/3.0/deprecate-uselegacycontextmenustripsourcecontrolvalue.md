---
ms.openlocfilehash: df6169289fb96df5f7daf8bd58ccaeebc33ad87c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556145"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換

`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`.Net Core 或 .net 5.0 和更新版本的 Windows Forms 不支援 .NET Framework 4.7.2 中引進的相容性參數。

#### <a name="change-description"></a>變更描述

從 .NET Framework 4.7.2 開始， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 相容性參數可讓開發人員選擇不使用屬性的新行為 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> ，這現在會傳回原始檔控制的參考。 屬性的先前行為是傳回 `null` 。 如需詳細資訊，請參閱[ \<AppContextSwitchOverrides> 元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET Core 和 .NET 5.0 和更新版本中， `Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue` 不支援此參數。

#### <a name="version-introduced"></a>引進的版本

3.0

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
