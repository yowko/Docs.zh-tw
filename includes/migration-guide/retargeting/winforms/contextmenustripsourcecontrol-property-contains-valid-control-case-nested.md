---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606707"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>在巢狀 ToolStripMenuItems 的情況下，ContextMenuStrip.SourceControl 屬性包含有效的控制項

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和舊版本中，當使用者從巢狀 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項開啟功能表時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性會誤傳回 null。 在 .NET Framework 4.7.2 和更新版本中，一律會將 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 屬性設定為實際的來源控制項。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更** 為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。
- 以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)，並將其設定為 `false`，如下範例所示。

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版的行為，則可以明確將此 AppContext 參數設為 `true`，選擇使用舊版的來源控制項。

| 名稱    | 值       |
|:--------|:------------|
| 範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
