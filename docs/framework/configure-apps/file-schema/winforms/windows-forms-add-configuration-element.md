---
title: Windows Form 加入組態項目
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eca84aa3a3d7bffaac31cc36ed14e5d5bb5a37cc
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788475"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Form 加入組態項目

`<add>`元素會將預先定義的索引鍵，指定您的 Windows Form 應用程式是否支援新增至 Windows Forms 應用程式在.NET Framework 4.7 或更新版本的功能。

## <a name="syntax"></a>語法

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

| 屬性 | 描述 |
| --------- | ----------- |
| `key`     | 必要屬性。 預先定義的索引鍵名稱對應至特定的 Windows Forms 可自訂的功能。 |
| `value`   | 必要屬性。 要指派給值`key`。 |

### <a name="key-attribute-names-and-associated-values"></a>`key` 屬性名稱和相關聯的值

| `key` 名稱 | 值 | 描述 |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否在單一行程中縮放錨定的控制項。 "true"停用單一傳遞調整;否則為 false。 請參閱 「 單一成功調整 」 一節[備註](#remarks)如需詳細資訊。 |
| 「 DpiAwareness" | "PerMonitorV2"&#124;"false" | 指出是否為 DPI 感知應用程式。 設定 「 PerMonitorV2"，以支援 Dpi 感知; 的索引鍵否則，請將它設定為"false"。 DPI 感知是選用的功能;若要利用 Windows Form 的高 DPI 支援，您應該設定其值以"PerMonitorV2 」。 請參閱[備註](#remarks)節的詳細資訊。 |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.CheckedListBox>控制項利用的調整和配置.NET Framework 4.7 中引入的改進功能。 "true"退出 caling 和版面配置的增強功能;否則即為"false"。 |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.DataGridView>控制調整和配置採用的.NET Framework 4.7 中的增強功能。 若要退出 DPI 感知;"true""false"否則。 |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true"以選擇退出接收 DPI 縮放比例變更與相關的訊息"false"否則。 請參閱[備註](#remarks)節的詳細資訊。 |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | 表示在 Windows Forms 應用程式會自動調整大小由於 DPI 縮放比例的變更。 若要啟用自動調整大小;"true"否則為 false。 |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.Form>相應縮小單一行程。 調整;"true"停用單一行程否則為 false。 請參閱 「 單一成功調整 」 一節[備註](#remarks)如需詳細資訊。 |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.MonthCalendar>在單一行程中縮放控制項。 調整;"true"停用單一行程否則為 false。 請參閱 「 單一成功調整 」 一節[備註](#remarks)如需詳細資訊。 |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.ToolStrip>控制項利用的調整和配置.NET Framework 4.7 中引入的改進功能。 若要退出 DPI 感知;"true""false"否則。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | 設定新的 Windows Forms 應用程式功能的支援。 |

## <a name="remarks"></a>備註

從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。

`<System.Windows.Forms.ApplicationConfigurationSection>`項目可讓您新增一或多個子`<add>`項目，其中每一個定義特定的組態設定。

如需 Windows Form 中的高 DPI 支援的概觀，請參閱 <<c0> [ 在 Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。

### <a name="dpiawareness"></a>DpiAwareness

從.NET Framework 4.7 開始從 Windows 10 Creators 版和.NET Framework 版本為目標的 Windows 版本之下執行的 Windows Forms 應用程式可以設定為充分利用.NET Framework 中引進的高 DPI 改良功能4.7。 它們包括：

- 已啟動的 Windows Forms 應用程式之後變更的 DPI 或小數位數的比例的使用者的動態 DPI 案例的支援。

- 改進調整和配置數個 Windows Form 控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。

高 DPI 感知是選用的功能;根據預設，windows 7`DpiAwareness`是`false`。 您可以選擇將 Windows Form 支援 DPI 感知此機碼值設`PerMonitorV2`應用程式組態檔中。 如果啟用 DPI 感知，則也會啟用所有個別的 DPI 功能。 它們包括：

- DPI 變更訊息，就會受`DisableDpiChangedMessageHandling`索引鍵。

- 動態 DPI 支援，由控制`EnableWindowsFormsHighDpiAutoResizing`索引鍵。

- 單一行程控制項縮放比例，這會受到`Form.DisableSinglePassControlScaling`針對個別<xref:System.Windows.Forms.Form>控制項，藉由`AnchorLayout.DisableSinglePassControlScaling`錨定的控制項，以及索引鍵`MonthCalendar.DisableSinglePassControlScaling`金鑰<xref:System.Windows.Forms.MonthCalendar>控制項

- 高 DPI 縮放比例和版面配置的增強功能，會受到`CheckListBox.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.CheckedListBox>控制項，藉由`DataGridView.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.DataGridView>控制項，並依據`Toolstrip.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.ToolStrip>控制項。

提供藉由設定選擇加入設定一個預設`DpiAwareness`至`PerMonitorV2`通常適用於新的 Windows Forms 應用程式。 不過，您可以再退出個別的高 DPI 改進應用程式組態檔中加入對應的索引鍵。 比方說，若要使用的所有動態 DPI 支援除了新 DPI 功能，您可以加入下列應用程式組態檔來：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

一般而言，您選擇退出特定功能因為您已選擇要以程式設計方式處理它。

如需利用 Windows Forms 應用程式中的高 DPI 支援的詳細資訊，請參閱[在 Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

從.NET Framework 4.7 開始，Windows Form 控制項引發的 DPI 縮放比例的變更相關的事件數目。 其中包括<xref:System.Windows.Forms.Control.DpiChangedAfterParent>， <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，和<xref:System.Windows.Forms.Form.DpiChanged>事件。 值`DisableDpiChangedMessageHandling`金鑰會決定在 Windows Forms 應用程式是否會引發這些事件。

### <a name="single-pass-scaling"></a>單一行程調整

它們會隨相應單一或多階段調整影響的使用者介面的認知回應能力和視覺外觀的使用者介面項目。 從.NET Framework 4.7 開始，Windows Form 會使用單一行程調整。 在舊版的.NET Framework 中，透過多個行程，這造成一些控制項進行調整，多個必須執行調整。 單一行程調整應該才可停用舊的行為取決於您的應用程式。

## <a name="see-also"></a>另請參閱

- [Windows Forms 組態區段](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)
- [Windows Forms 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
