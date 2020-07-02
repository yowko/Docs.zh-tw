---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614400"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>在巢狀 ToolStripMenuItems 的情況下，ContextMenuStrip.SourceControl 屬性包含有效的控制項

#### <a name="details"></a>詳細資料

在 .NET Framework 4.7.1 和舊版本中，當使用者從巢狀 <xref:System.Windows.Forms.ToolStripMenuItem> 控制項開啟功能表時，<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> 屬性會誤傳回 null。 在 .NET Framework 4.7.2 和更新版本中，一律會將 <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> 屬性設定為實際的來源控制項。

#### <a name="suggestion"></a>建議

**如何加入宣告或退出這些變更**為了讓應用程式受益于這些變更，它必須在 .NET Framework 4.7.2 或更新版本上執行。 應用程式可以用下列任一種方式受益於這些變更：

- 以 .NET Framework 4.7.2 為目標。 在以 .NET Framework 4.7.2 或更新版本為目標的 Windows Forms 應用程式上，預設會啟用這項變更。
- 以 .NET Framework 4.7.1 或舊版為目標，並選擇不使用舊版協助工具行為；方法為在 app.config 檔的 `<runtime>` 區段中新增下列 [AppContext 參數](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element)，並將其設定為 `false`，如下範例所示。

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

如果應用程式是以 .NET Framework 4.7.2 或更新版本為目標，而您想要保留舊版的行為，則可以明確將此 AppContext 參數設為 `true`，選擇使用舊版的來源控制項。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.7.2       |
| 類型    | 正在重定目標 |

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
