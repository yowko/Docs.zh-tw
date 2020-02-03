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
# <a name="printpreviewdialog-control-overview-windows-forms"></a><span data-ttu-id="08113-102">PrintPreviewDialog 控制項總覽（Windows Forms）</span><span class="sxs-lookup"><span data-stu-id="08113-102">PrintPreviewDialog control overview (Windows Forms)</span></span>

<span data-ttu-id="08113-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> 控制項是預先設定的對話方塊，用來顯示[PrintDocument](printdocument-component-windows-forms.md)在列印時的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="08113-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> control is a pre-configured dialog box used to display how a [PrintDocument](printdocument-component-windows-forms.md) will appear when printed.</span></span> <span data-ttu-id="08113-104">在以 Windows 為基礎的應用程式中使用它做為簡單的解決方案，而不是設定自己的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="08113-104">Use it within your Windows-based application as a simple solution instead of configuring your own dialog box.</span></span> <span data-ttu-id="08113-105">這個控制項包含列印、放大、顯示一或多頁及關閉對話方塊等按鈕。</span><span class="sxs-lookup"><span data-stu-id="08113-105">The control contains buttons for printing, zooming in, displaying one or multiple pages, and closing the dialog box.</span></span>

## <a name="key-properties-and-methods"></a><span data-ttu-id="08113-106">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="08113-106">Key properties and methods</span></span>

<span data-ttu-id="08113-107">控制項的索引鍵屬性是 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>，它會設定要預覽的檔。</span><span class="sxs-lookup"><span data-stu-id="08113-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="08113-108">檔必須是 <xref:System.Drawing.Printing.PrintDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="08113-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="08113-109">為了顯示對話方塊，您必須呼叫其 <xref:System.Windows.Forms.Form.ShowDialog%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="08113-109">In order to display the dialog box, you must call its <xref:System.Windows.Forms.Form.ShowDialog%2A> method.</span></span> <span data-ttu-id="08113-110">消除鋸齒可以讓文字看起來更平滑，但也可以讓顯示器變慢;若要使用它，請將 <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> 屬性設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="08113-110">Anti-aliasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> property to `true`.</span></span>

<span data-ttu-id="08113-111">某些屬性可透過 <xref:System.Windows.Forms.PrintPreviewDialog> 所包含的 <xref:System.Windows.Forms.PrintPreviewControl> 取得。</span><span class="sxs-lookup"><span data-stu-id="08113-111">Certain properties are available through the <xref:System.Windows.Forms.PrintPreviewControl> that the <xref:System.Windows.Forms.PrintPreviewDialog> contains.</span></span> <span data-ttu-id="08113-112">（您不需要將此 <xref:System.Windows.Forms.PrintPreviewControl> 加入表單中; 當您將對話方塊新增至表單時，它就會自動包含在 <xref:System.Windows.Forms.PrintPreviewDialog> 中）。<xref:System.Windows.Forms.PrintPreviewControl> 可用的屬性範例為 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 和 <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> 屬性，可決定在控制項上水準和垂直顯示的頁面數目。</span><span class="sxs-lookup"><span data-stu-id="08113-112">(You do not have to add this <xref:System.Windows.Forms.PrintPreviewControl> to the form; it is automatically contained within the <xref:System.Windows.Forms.PrintPreviewDialog> when you add the dialog to your form.) Examples of properties available through the <xref:System.Windows.Forms.PrintPreviewControl> are the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties, which determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="08113-113">您可以在 Visual Basic、Visual C#中的 `printPreviewDialog1.PrintPreviewControl.Columns` 或 visual C++中的 `printPreviewDialog1->PrintPreviewControl->Columns` 中，存取 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> 屬性做為 `PrintPreviewDialog1.PrintPreviewControl.Columns`。</span><span class="sxs-lookup"><span data-stu-id="08113-113">You can access the <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> property as `PrintPreviewDialog1.PrintPreviewControl.Columns` in Visual Basic, `printPreviewDialog1.PrintPreviewControl.Columns` in Visual C#, or `printPreviewDialog1->PrintPreviewControl->Columns` in Visual C++.</span></span>

## <a name="printpreviewdialog-performance"></a><span data-ttu-id="08113-114">PrintPreviewDialog 效能</span><span class="sxs-lookup"><span data-stu-id="08113-114">PrintPreviewDialog performance</span></span>

<span data-ttu-id="08113-115">在下列情況下，<xref:System.Windows.Forms.PrintPreviewDialog> 控制項的初始化速度非常緩慢：</span><span class="sxs-lookup"><span data-stu-id="08113-115">Under the following conditions, the <xref:System.Windows.Forms.PrintPreviewDialog> control initializes very slowly:</span></span>

- <span data-ttu-id="08113-116">會使用網路印表機。</span><span class="sxs-lookup"><span data-stu-id="08113-116">A network printer is used.</span></span>
- <span data-ttu-id="08113-117">系統會修改此印表機的使用者喜好設定（例如雙工設定）。</span><span class="sxs-lookup"><span data-stu-id="08113-117">User preferences for this printer, such as duplex settings, are modified.</span></span>

<span data-ttu-id="08113-118">針對在 .NET Framework 4.5.2 上執行的應用程式，您可以將下列機碼新增至設定檔的 \<appSettings > 區段，以改善 <xref:System.Windows.Forms.PrintPreviewDialog> 控制項初始化的效能：</span><span class="sxs-lookup"><span data-stu-id="08113-118">For apps running on the .NET Framework 4.5.2, you can add the following key to the \<appSettings> section of your configuration file to improve the performance of <xref:System.Windows.Forms.PrintPreviewDialog> control initialization:</span></span>

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```

<span data-ttu-id="08113-119">如果 `EnablePrintPreviewOptimization` 索引鍵設定為任何其他值，或索引鍵不存在，則不會套用優化。</span><span class="sxs-lookup"><span data-stu-id="08113-119">If the `EnablePrintPreviewOptimization` key is set to any other value, or if the key is not present, the optimization is not applied.</span></span>

<span data-ttu-id="08113-120">針對在 .NET Framework 4.6 或更新版本上執行的應用程式，您可以將下列參數新增至應用程式佈建檔的[\<runtime >](../../configure-apps/file-schema/runtime/index.md)區段中的[\<AppCoNtextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)元素：</span><span class="sxs-lookup"><span data-stu-id="08113-120">For apps running on the .NET Framework 4.6 or later versions, you can add the following switch to the [\<AppContextSwitchOverrides>](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [\<runtime>](../../configure-apps/file-schema/runtime/index.md) section of your app config file:</span></span>

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
```

<span data-ttu-id="08113-121">如果參數不存在或設定為任何其他值，則不會套用優化。</span><span class="sxs-lookup"><span data-stu-id="08113-121">If the switch is not present or if it is set to any other value, the optimization is not applied.</span></span>

<span data-ttu-id="08113-122">如果您使用 <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> 事件來修改印表機設定，即使已設定優化設定參數，<xref:System.Windows.Forms.PrintPreviewDialog> 控制項的效能也不會改善。</span><span class="sxs-lookup"><span data-stu-id="08113-122">If you use the <xref:System.Drawing.Printing.PrintDocument.QueryPageSettings> event to modify printer settings, the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> control will not improve even if an optimization configuration switch is set.</span></span>

## <a name="see-also"></a><span data-ttu-id="08113-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08113-123">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewDialog>
- [<span data-ttu-id="08113-124">PrintPreviewControl 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="08113-124">PrintPreviewControl Control Overview</span></span>](printpreviewcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="08113-125">PrintPreviewDialog 控制項</span><span class="sxs-lookup"><span data-stu-id="08113-125">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="08113-126">對話方塊控制項和元件</span><span class="sxs-lookup"><span data-stu-id="08113-126">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
