---
title: Windows Forms 新增設定元素
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
ms.openlocfilehash: dc1786f1f2dcc7bd01488dd24c6ef454f7e1cfbd
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557628"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms 新增設定元素

`<add>`元素會新增預先定義的索引鍵，以指定您的 Windows Form 應用程式是否支援 .NET Framework 4.7 或更新版本中新增至 Windows Forms 應用程式的功能。

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
| `key`     | 必要屬性。 預先定義的索引鍵名稱，對應至特定的 Windows Forms 可自訂功能。 |
| `value`   | 必要屬性。 要指派給 `key` 的值。 |

### <a name="key-attribute-names-and-associated-values"></a>`key` 屬性名稱和相關聯的值

| `key` 名稱 | 值 | 描述 |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true" &#124; "false" | 指出錨定控制項是否在單一行程中縮放。 "true" 表示停用單一行程調整;否則為 false。 如需詳細資訊，請參閱 [備註](#remarks) 中的「單一通過調整」一節。 |
| "DpiAwareness" | "PerMonitorV2" &#124; "false" | 指出應用程式是否為 DPI 感知。 將金鑰設為 "PerMonitorV2" 以支援 Dpi 感知;否則，請將它設定為 "false"。 DPI 感知是可加入宣告的功能;若要利用 Windows Forms 的高 DPI 支援，您應將其值設定為 "PerMonitorV2"。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。 |
| "CheckedListBox. DisableHighDpiImprovements" | "true" &#124; "false" | 指出控制項是否 <xref:System.Windows.Forms.CheckedListBox> 會利用 .NET Framework 4.7 中引進的調整和版面配置增強功能。 "true" 表示退出調整和版面配置改善;否則為 "false"。 |
| "DisableHighDpiImprovements" | "true" &#124; "false" | 指出 <xref:System.Windows.Forms.DataGridView> .NET Framework 4.7 中引進的控制項縮放和版面配置改善。 "true" 表示退出 DPI 感知;否則為 "false"。 |
| "DisableDpiChangedMessageHandling" | "true" &#124; "false" | "true" 表示選擇不接受與 DPI 調整變更相關的訊息;否則為 "false"。 如需詳細資訊，請參閱「 [備註](#remarks) 」一節。 |
| >enablewindowsformshighDPIautoresizing | "true" &#124; "false" | 指出 Windows Forms 的應用程式是否因為 DPI 縮放比例變更而自動調整大小。 "true" 表示啟用自動調整大小;否則為 false。 |
| "DisableSinglePassControlScaling" | "true" &#124; "false" | 指出是否 <xref:System.Windows.Forms.Form> 在單一行程中縮放。 "true" 表示停用單一傳遞調整;否則為 false。 如需詳細資訊，請參閱 [備註](#remarks) 中的「單一通過調整」一節。 |
| "MonthCalendar. DisableSinglePassControlScaling" | "true" &#124; "false" | 指出控制項是否 <xref:System.Windows.Forms.MonthCalendar> 在單一行程中縮放。 "true" 表示停用單一傳遞調整;否則為 false。 如需詳細資訊，請參閱 [備註](#remarks) 中的「單一通過調整」一節。 |
| "Toolstrip. DisableHighDpiImprovements" | "true" &#124; "false" | 指出控制項是否 <xref:System.Windows.Forms.ToolStrip> 會利用 .NET Framework 4.7 中引進的調整和版面配置增強功能。 "true" 表示退出 DPI 感知;否則為 "false"。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 項目 | 描述 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | 設定新 Windows Forms 應用程式功能的支援。 |

## <a name="remarks"></a>備註

從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。

`<System.Windows.Forms.ApplicationConfigurationSection>`元素可讓您新增一或多個子 `<add>` 元素，而每個專案都會定義特定的設定。

如需 Windows Forms 高 DPI 支援的總覽，請參閱 [Windows Forms 中的高 Dpi 支援](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)。

### <a name="dpiawareness"></a>DpiAwareness

在 Windows 版本下執行的 Windows Forms 應用程式，從 Windows 10 建立者版本開始，以及從 .NET Framework 4.7 開始的 .NET Framework 目標版本，都可以設定為利用 .NET Framework 4.7 中所引進的高 DPI 增強功能。 它們包括：

- 支援動態 DPI 案例，在此案例中，使用者會在 Windows Forms 應用程式啟動之後變更 DPI 或縮放比例。

- 改善許多 Windows Forms 控制項（例如控制項和控制項）的縮放比例和版面配置 <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> 。

高 DPI 感知是可加入宣告的功能;根據預設，的值 `DpiAwareness` 為 `false` 。 您可以藉由將此索引鍵的值設定為 `PerMonitorV2` 應用程式佈建檔中的值，來加入宣告 Windows Forms 的 DPI 感知支援。 如果啟用 DPI 感知，則也會啟用所有個別的 DPI 功能。 它們包括：

- 由索引鍵控制的 DPI 變更訊息 `DisableDpiChangedMessageHandling` 。

- 動態 DPI 支援，由索引 `EnableWindowsFormsHighDpiAutoResizing` 鍵控制。

- 單一傳遞控制項調整，由 `Form.DisableSinglePassControlScaling` 針對個別 <xref:System.Windows.Forms.Form> 控制項、 `AnchorLayout.DisableSinglePassControlScaling` 錨定控制項的索引鍵，以及控制項的索引 `MonthCalendar.DisableSinglePassControlScaling` 鍵 <xref:System.Windows.Forms.MonthCalendar> 所控制

- 高 DPI 縮放比例和版面配置增強功能，由控制項的索引 `CheckListBox.DisableHighDpiImprovements` 鍵 <xref:System.Windows.Forms.CheckedListBox> 、控制項的索引鍵 `DataGridView.DisableHighDpiImprovements` <xref:System.Windows.Forms.DataGridView> ，以及 `Toolstrip.DisableHighDpiImprovements` 控制項的按鍵 <xref:System.Windows.Forms.ToolStrip> 來控制。

設定為所提供的單一預設加入宣告設定 `DpiAwareness` ， `PerMonitorV2` 通常適合新的 Windows Forms 應用程式。 不過，您可以藉由將對應的金鑰新增至應用程式佈建檔，來退出個別的高 DPI 改善。 例如，若要利用除了動態 DPI 支援以外的所有新 DPI 功能，您可以將下列內容新增至您的應用程式佈建檔：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

您通常會退出宣告特定功能，因為您已選擇以程式設計方式處理它。

如需在 Windows Forms 應用程式中充分利用高 DPI 支援的詳細資訊，請參閱 [Windows Forms 中的高 Dpi 支援](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)。

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

從 .NET Framework 4.7 開始，Windows Forms 控制項會引發一些與 DPI 縮放比例變更相關的事件。 其中包括 <xref:System.Windows.Forms.Control.DpiChangedAfterParent> 、 <xref:System.Windows.Forms.Control.DpiChangedBeforeParent> 和 <xref:System.Windows.Forms.Form.DpiChanged> 事件。 索引鍵的值 `DisableDpiChangedMessageHandling` 會決定是否在 Windows Forms 應用程式中引發這些事件。

### <a name="single-pass-scaling"></a>單一階段調整

單一或多階段調整會影響使用者介面的觀察回應能力，以及使用者介面專案在縮放時的視覺外觀。 從 .NET Framework 4.7 開始，Windows Forms 使用單一通過調整。 在舊版的 .NET Framework 中，調整是透過多個行程執行，這會導致某些控制項的縮放比例超過所需。 只有當您的應用程式相依于舊的行為時，才應停用單一傳遞調整。

## <a name="see-also"></a>另請參閱

- [Windows Forms 設定區段](index.md)
- [Windows Forms 中的高 DPI 支援](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)
