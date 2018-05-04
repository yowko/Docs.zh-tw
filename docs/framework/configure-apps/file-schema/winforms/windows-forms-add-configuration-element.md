---
title: Windows Form 加入組態項目
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 529dbccd5ddb4dd1f1456fb9a6043f3c5f7b378d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="windows-forms-add-configuration-element"></a>Windows Form 加入組態項目

`<add>`項目加入預先定義的索引鍵，指定您的 Windows Form 應用程式是否支援加入.NET Framework 4.7 在或更新版本的 Windows Forms 應用程式的功能。

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
| `key`     | 必要屬性。 預先定義的索引鍵名稱對應至特定的 Windows Form 可自訂功能。 |
| `value`   | 必要屬性。 要指派給值`key`。 |

### <a name="key-attribute-names-and-associated-values"></a>`key` 屬性名稱和相關聯的值

| `key` 名稱 | 值 | 描述 |
| ---------- | ------ | ----------- |
| 「 AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否錨定的控制項在單一行程中縮放。 若要停用單一"true"傳遞縮放比例。否則為 false。 請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。 |
| 「 DpiAwareness" | 「 PerMonitorV2"&#124;"false" | 指出是否為 DPI 感知應用程式。 設定"PerMonitorV2 」 支援 Dpi 感知; 的索引鍵否則，將它設定為"false"。 DPI 感知是選擇性功能。若要利用 Windows Form 高 DPI 支援，您應該將其值設"PerMonitorV2"。 請參閱[備註](#remarks)節的詳細資訊。 |
| 「 CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.CheckedListBox>控制項利用.NET Framework 4.7 中導入的縮放比例和配置增強功能。 "true"退出 caling 和配置的增強功能;否則，"false"。 |
| 「 DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.DataGridView>控制.NET Framework 4.7 中導入的縮放比例和配置增強功能。 "true"退出 DPI 感知;"false"否則。 |
| 「 DisableDpiChangedMessageHandling" | "true"&#124;"false" | "true"退出接收 DPI 縮放比例; 的變更與相關的訊息"false"否則。 請參閱[備註](#remarks)節的詳細資訊。 |
| 「 EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | 表示在 Windows Forms 應用程式會自動調整大小因為 DPI 縮放比例變更。 若要啟用自動調整大小;"true"否則為 false。 |
| 「 Form.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.Form>調整在單一行程中。 縮放比例;"true"停用單一行程否則為 false。 請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。 |
| 「 MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.MonthCalendar>在單一行程中縮放控制項。 縮放比例;"true"停用單一行程否則為 false。 請參閱中的 「 單一傳遞調整 」 一節[備註](#Remarks)如需詳細資訊。 |
| 「 Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | 指出是否<xref:System.Windows.Forms.ToolStrip>控制項利用.NET Framework 4.7 中導入的縮放比例和配置增強功能。 "true"退出 DPI 感知;"false"否則。 |

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

| 元素 | 描述 |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | 設定新的 Windows Form 應用程式功能的支援。 |

## <a name="a-nameremarks--remarks"></a><a name="remarks" /> 註解

從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。 

`<System.Windows.Forms.ApplicationConfigurationSection>`元素可讓您新增一個以上的子系`<add>`項目，其中每個定義特定的組態設定。  

如需 Windows Form 高 DPI 支援的概觀，請參閱[Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。

### <a name="dpiawareness"></a>DpiAwareness

從.NET Framework 4.7 下開頭為 Windows 10 建立者 Edition 和.NET Framework 目標版本的 Windows 版本所執行的 Windows Forms 應用程式可以設定為充分利用.NET Framework 中引進的高 DPI 改良功能4.7。 它們包括：

- 支援動態 DPI 案例，已啟動的 Windows Form 應用程式之後變更 DPI 或小數位數因素的使用者。

- 改良的縮放比例和 Windows Form 的數字的版面配置控制項，例如<xref:System.Windows.Forms.MonthCalendar>控制項和<xref:System.Windows.Forms.CheckedListBox>控制項。 

高 DPI 感知是選擇性功能。根據預設，值`DpiAwareness`是`false`。 您可以選擇為 Windows Form 支援 DPI 感知藉由設定此機碼值`PerMonitorV2`應用程式組態檔中。 如果啟用 DPI 感知，則也會啟用所有的個別 DPI 功能。 它們包括：

- DPI 變更所控制的訊息`DisableDpiChangedMessageHandling`索引鍵。

- 動態 DPI 支援，由`EnableWindowsFormsHighDpiAutoResizing`索引鍵。

- 單次控制項縮放比例，這由`Form.DisableSinglePassControlScaling`個別<xref:System.Windows.Forms.Form>控制項，藉由`AnchorLayout.DisableSinglePassControlScaling`錨定的控制項，以及索引鍵`MonthCalendar.DisableSinglePassControlScaling`金鑰<xref:System.Windows.Forms.MonthCalendar>控制項 

- 高 DPI 縮放比例和配置的增強功能，由`CheckListBox.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.CheckedListBox>藉由控制`DataGridView.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.DataGridView>控制項，並依據`Toolstrip.DisableHighDpiImprovements`金鑰<xref:System.Windows.Forms.ToolStrip>控制項。  

提供藉由設定中，選擇設定單一預設`DpiAwareness`至`PerMonitorV2`通常適合新的 Windows Form 應用程式。 不過，您可以再退出個別的高 DPI 改進將對應的索引鍵加入至應用程式組態檔。 比方說，若要利用所有除了動態 DPI 支援新 DPI featuers，您可以加入下列應用程式組態檔：

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <--! Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```
一般而言，您退出特定功能因為您已選擇要以程式設計方式處理。

如需如何利用 Windows Form 應用程式中的高 DPI 支援的詳細資訊，請參閱[Windows Form 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)。
 
### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

從.NET Framework 4.7 開始，Windows Form 控制項引發的 DPI 縮放比例的變更相關的事件數目。 這些包括<xref:System.Windows.Forms.Control.DpiChangedAfterParent>， <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>，和<xref:System.Windows.Forms.Form.DpiChanged>事件。 值`DisableDpiChangedMessageHandling`機碼決定是否在 Windows Form 應用程式中引發這些事件。 

### <a name="single-pass-scaling"></a>單次縮放比例

這些調整單一或多個行程調整影響使用者介面的認知的回應和視覺外觀的使用者介面項目。 從.NET Framework 4.7 開始，Windows Form 會使用單一行程縮放比例。 在舊版的.NET Framework 中，透過多個行程，這造成部分控制項，以調整多個必須執行縮放比例。 單一行程調整應該才可停用舊的行為取決於您的應用程式。  

## <a name="see-also"></a>另請參閱
 
[Windows Form 的組態區段](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)   
[Windows Forms 中的高 DPI 支援](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
