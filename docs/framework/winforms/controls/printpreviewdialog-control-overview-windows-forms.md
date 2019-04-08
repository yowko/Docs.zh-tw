---
title: PrintPreviewDialog 控制項概觀 (Windows Form)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32fbdd222e34f642d29255e6c594076b6d2a91e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188834"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog 控制項概觀 (Windows Form)
Windows Forms<xref:System.Windows.Forms.PrintPreviewDialog>控制項是預先設定的對話方塊，用來顯示如何[PrintDocument](printdocument-component-windows-forms.md)列印時，會出現。 您可以使用它在您以 Windows 為基礎的應用程式，做為簡單的解決方案，而不是設定您自己的對話方塊。 這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。  
  
## <a name="key-properties-and-methods"></a>索引鍵屬性和方法  
 控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，可設定要預覽的文件。 必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。 若要顯示對話方塊，您必須呼叫其<xref:System.Windows.Forms.Form.ShowDialog%2A>方法。 消除鋸齒可以讓文字出現更順暢，但可能也會使速度較慢; 顯示若要使用它，將<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>屬性設`true`。  
  
 某些屬性都是透過<xref:System.Windows.Forms.PrintPreviewControl>，<xref:System.Windows.Forms.PrintPreviewDialog>包含。 (您沒有新增這<xref:System.Windows.Forms.PrintPreviewControl>表單中; 它會自動包含在<xref:System.Windows.Forms.PrintPreviewDialog>將對話方塊新增至您的表單。)屬性可透過範例<xref:System.Windows.Forms.PrintPreviewControl>都<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性，負責決定控制項上顯示水平和垂直的頁數。 您可以存取<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>屬性設為`PrintPreviewDialog1.PrintPreviewControl.Columns`在 Visual Basic`printPreviewDialog1.PrintPreviewControl.Columns`視覺效果中C#，或`printPreviewDialog1->PrintPreviewControl->Columns`中[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]。  
  
## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog 效能

在下列情況中，<xref:System.Windows.Forms.PrintPreviewDialog>控制項初始化速度很慢：

- 會使用網路印表機。
- 會修改這個印表機，雙面列印設定，例如使用者喜好設定。
  
針對.NET Framework 4.5.2 上執行的應用程式，您可以新增至下列機碼\<appSettings > 您的組態檔，以改善效能的區段<xref:System.Windows.Forms.PrintPreviewDialog>控制初始設定：

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
如果`EnablePrintPreviewOptimization`機碼設為任何其他值，或如果索引鍵不存在，最佳化不會套用。

.NET Framework 4.6 或更新版本上執行的應用程式，您可以新增下列參數到[ \<Appcontextswitchoverrides> >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[ \<runtime >](../../configure-apps/file-schema/runtime/index.md)您的應用程式組態檔區段：

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
如果參數不存在，或它設定為任何其他值，不會套用最佳化。 

如果您使用<xref:System.Drawing.Printing.PrintDocument.QueryPageSettings>若要修改的印表機設定 的效能事件<xref:System.Windows.Forms.PrintPreviewDialog>即使最佳化組態參數設定不會改善控制項。  

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [PrintPreviewControl 控制項概觀](printpreviewcontrol-control-overview-windows-forms.md)
- [PrintPreviewDialog 控制項](printpreviewdialog-control-windows-forms.md)
- [對話方塊控制項和元件](dialog-box-controls-and-components-windows-forms.md)
