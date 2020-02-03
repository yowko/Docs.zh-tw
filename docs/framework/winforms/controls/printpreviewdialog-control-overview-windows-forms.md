---
title: PrintPreviewDialog 控制項概觀
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
ms.openlocfilehash: 6fb971493336cda1e04c720dd09147e650918c3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741418"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog 控制項總覽（Windows Forms）

Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> 控制項是預先設定的對話方塊，用來顯示[PrintDocument](printdocument-component-windows-forms.md)在列印時的顯示方式。 在以 Windows 為基礎的應用程式中使用它做為簡單的解決方案，而不是設定自己的對話方塊。 這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。

## <a name="key-properties-and-methods"></a>索引鍵屬性和方法

控制項的索引鍵屬性是 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，它會設定要預覽的檔。 檔必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。 為了顯示對話方塊，您必須呼叫其 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法。 消除鋸齒可以讓文字看起來更平滑，但也可以讓顯示器變慢;若要使用它，請將 <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> 屬性設定為 [`true`]。

某些屬性可透過 <xref:System.Windows.Forms.PrintPreviewDialog> 所包含的 <xref:System.Windows.Forms.PrintPreviewControl> 取得。 （您不需要將此 <xref:System.Windows.Forms.PrintPreviewControl> 加入表單中; 當您將對話方塊新增至表單時，它就會自動包含在 <xref:System.Windows.Forms.PrintPreviewDialog> 中）。<xref:System.Windows.Forms.PrintPreviewControl> 可用的屬性範例為 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 和 <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> 屬性，可決定在控制項上水準和垂直顯示的頁面數目。 您可以在 Visual Basic、Visual C#中的 `printPreviewDialog1.PrintPreviewControl.Columns` 或 visual C++中的 `printPreviewDialog1->PrintPreviewControl->Columns` 中，存取 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 屬性做為 `PrintPreviewDialog1.PrintPreviewControl.Columns`。

## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog 效能

在下列情況下，<xref:System.Windows.Forms.PrintPreviewDialog> 控制項的初始化速度非常緩慢：

- 會使用網路印表機。
- 系統會修改此印表機的使用者喜好設定（例如雙工設定）。

針對在 .NET Framework 4.5.2 上執行的應用程式，您可以將下列機碼新增至設定檔的 \<appSettings > 區段，以改善 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項初始化的效能：

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

如果 `EnablePrintPreviewOptimization` 索引鍵設定為任何其他值，或索引鍵不存在，則不會套用優化。

針對在 .NET Framework 4.6 或更新版本上執行的應用程式，您可以將下列參數新增至應用程式佈建檔的[\<runtime >](../../configure-apps/file-schema/runtime/index.md)區段中的[\<AppCoNtextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)元素：

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

如果參數不存在或設定為任何其他值，則不會套用優化。

如果您使用 <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> 事件來修改印表機設定，即使已設定優化設定參數，<xref:System.Windows.Forms.PrintPreviewDialog> 控制項的效能也不會改善。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl 控制項概觀](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog 控制項](printpreviewdialog-control-windows-forms.md)
- [對話方塊控制項和元件](dialog-box-controls-and-components-windows-forms.md)
