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
ms.openlocfilehash: 0946220017fb78775f045bb225d84ea95aecd06b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538333"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="bf29e-102">PrintPreviewDialog 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="bf29e-102">PrintPreviewDialog control overview (Windows Forms)</span></span>
<span data-ttu-id="bf29e-103">Windows Form<xref:System.Windows.Forms.PrintPreviewDialog>控制項是預先設定的對話方塊，用來顯示如何[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)列印時。</span><span class="sxs-lookup"><span data-stu-id="bf29e-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="bf29e-104">該應用程式中使用 windows 做為簡單的解決方案，而不是設定您自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bf29e-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="bf29e-105">這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。</span><span class="sxs-lookup"><span data-stu-id="bf29e-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="bf29e-106">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="bf29e-106">Key properties and methods</span></span>  
 <span data-ttu-id="bf29e-107">控制項的索引鍵屬性是<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，它會設定要預覽的文件。</span><span class="sxs-lookup"><span data-stu-id="bf29e-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="bf29e-108">必須是文件<xref:System.Drawing.Printing.PrintDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="bf29e-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="bf29e-109">為了顯示對話方塊，您必須呼叫其<xref:System.Windows.Forms.Form.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="bf29e-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="bf29e-110">消除鋸齒可以讓文字出現較平滑，但是它可以讓較慢; 顯示若要使用它，<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="bf29e-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="bf29e-111">某些屬性都是透過<xref:System.Windows.Forms.PrintPreviewControl>，<xref:System.Windows.Forms.PrintPreviewDialog>包含。</span><span class="sxs-lookup"><span data-stu-id="bf29e-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="bf29e-112">(您沒有加入此<xref:System.Windows.Forms.PrintPreviewControl>表單; 它會自動包含在<xref:System.Windows.Forms.PrintPreviewDialog>將對話方塊加入至表單。)可透過使用屬性的範例<xref:System.Windows.Forms.PrintPreviewControl>是<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>和<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>屬性，判斷在控制項上顯示水平及垂直的頁數。</span><span class="sxs-lookup"><span data-stu-id="bf29e-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="bf29e-113">您可以存取<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>屬性做為`PrintPreviewDialog1.PrintPreviewControl.Columns`在 Visual Basic 中`printPreviewDialog1.PrintPreviewControl.Columns`Visual C# 中，或`printPreviewDialog1->PrintPreviewControl->Columns`中[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf29e-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].</span></span>  
  
## <a name="printpreviewdialog-performance"></a><span data-ttu-id="bf29e-114">PrintPreviewDialog 效能</span><span class="sxs-lookup"><span data-stu-id="bf29e-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="bf29e-115">在下列情況中，<xref:System.Windows.Forms.PrintPreviewDialog>控制項非常緩慢初始化：</span><span class="sxs-lookup"><span data-stu-id="bf29e-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="bf29e-116">會使用網路印表機。</span><span class="sxs-lookup"><span data-stu-id="bf29e-116">A network printer is used.</span></span>
- <span data-ttu-id="bf29e-117">會修改此印表機，雙面列印設定，例如使用者喜好設定。</span><span class="sxs-lookup"><span data-stu-id="bf29e-117">User preferences for this printer, such as duplex settings, are modified.</span></span>
  
<span data-ttu-id="bf29e-118">在.NET Framework 4.5.2 上執行的應用程式，您可以加入下列機碼\<appSettings > 您的組態檔，以改善效能的區段<xref:System.Windows.Forms.PrintPreviewDialog>控制初始設定：</span><span class="sxs-lookup"><span data-stu-id="bf29e-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
<span data-ttu-id="bf29e-119">如果`EnablePrintPreviewOptimization`機碼設為任何其他值，或如果索引鍵不存在，最佳化不會套用。</span><span class="sxs-lookup"><span data-stu-id="bf29e-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="bf29e-120">.NET Framework 4.6 或更新版本上執行的應用程式，您可以加入下列參數： 要[ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)中的項目[\<執行階段 >](../../configure-apps/file-schema/runtime/index.md)您的應用程式組態檔區段：</span><span class="sxs-lookup"><span data-stu-id="bf29e-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
<span data-ttu-id="bf29e-121">如果參數不存在，或是設定為任何其他值，不會套用最佳化。</span><span class="sxs-lookup"><span data-stu-id="bf29e-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span> 

<span data-ttu-id="bf29e-122">如果您使用<xref:System.Drawing.Printing.PrintDocument.QueryPageSettings>修改印表機設定、 效能事件<xref:System.Windows.Forms.PrintPreviewDialog>控制項不會改善，即使已設定最佳化組態參數。</span><span class="sxs-lookup"><span data-stu-id="bf29e-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>  

## <a name="see-also"></a><span data-ttu-id="bf29e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf29e-123">See also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [<span data-ttu-id="bf29e-124">PrintPreviewControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bf29e-124">PrintPreviewControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="bf29e-125">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="bf29e-125">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="bf29e-126">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="bf29e-126">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
