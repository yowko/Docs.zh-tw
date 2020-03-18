---
ms.openlocfilehash: 5aca2b8b3ca6572194692888eae3c5614245b481
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937109"
---
### <a name="uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported"></a>不支援使用傳統內容功能表，提供資源控制值相容性開關

.NET 框架 4.7.2 中引入的`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`相容性開關在 .NET Core 3.0 上的 Windows 表單中不受支援。

#### <a name="change-description"></a>變更描述

從 .NET 框架 4.7.2`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`開始，相容性開關允許開發人員退出宣告<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>屬性的新行為，該行為現在返回對原始程式碼管理的引用。 屬性的先前行為是返回`null`。 有關詳細資訊，請參閱[\<應用上下文切換覆蓋>元素](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)。

在 .NET 內核`Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue`中，不支援交換器。

#### <a name="version-introduced"></a>介紹的版本

3.0 預覽 9

#### <a name="recommended-action"></a>建議的動作

卸下開關。 不支援該開關，並且沒有可用的替代功能。

#### <a name="category"></a>類別

Windows Forms

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Windows.Forms.ContextMenuStrip.SourceControl`

-->
