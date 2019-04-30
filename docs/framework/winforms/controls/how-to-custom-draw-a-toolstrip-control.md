---
title: HOW TO：自訂繪製 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 9b3d6b9391971d4c2d012345b96c2ed64d33a998
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052985"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a><span data-ttu-id="507eb-102">HOW TO：自訂繪製 ToolStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="507eb-102">How to: Custom Draw a ToolStrip Control</span></span>
<span data-ttu-id="507eb-103"><xref:System.Windows.Forms.ToolStrip> 控制項具有下列相關聯轉譯 (繪製) 類別的項目：</span><span class="sxs-lookup"><span data-stu-id="507eb-103">The <xref:System.Windows.Forms.ToolStrip> controls have the following associated rendering (painting) classes:</span></span>  
  
- <span data-ttu-id="507eb-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> 提供您作業系統的外觀和樣式。</span><span class="sxs-lookup"><span data-stu-id="507eb-104"><xref:System.Windows.Forms.ToolStripSystemRenderer> provides the appearance and style of your operating system.</span></span>  
  
- <span data-ttu-id="507eb-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> 提供 Microsoft Office 的外觀和樣式。</span><span class="sxs-lookup"><span data-stu-id="507eb-105"><xref:System.Windows.Forms.ToolStripProfessionalRenderer> provides the appearance and style of Microsoft Office.</span></span>  
  
- <span data-ttu-id="507eb-106"><xref:System.Windows.Forms.ToolStripRenderer> 為其他兩個呈現類別的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="507eb-106"><xref:System.Windows.Forms.ToolStripRenderer> is the abstract base class for the other two rendering classes.</span></span>  
  
 <span data-ttu-id="507eb-107">若要對 <xref:System.Windows.Forms.ToolStrip> 自訂繪圖 (也稱為主控描繪)，您可以覆寫其中一個轉譯器類別，並變更轉譯邏輯的層面。</span><span class="sxs-lookup"><span data-stu-id="507eb-107">To custom draw (also known as owner draw) a <xref:System.Windows.Forms.ToolStrip>, you can override one of the renderer classes and change an aspect of the rendering logic.</span></span>  
  
 <span data-ttu-id="507eb-108">下列程序會說明自訂繪圖的各種層面。</span><span class="sxs-lookup"><span data-stu-id="507eb-108">The following procedures describe various aspects of custom drawing.</span></span>  
  
### <a name="to-switch-between-the-provided-renderers"></a><span data-ttu-id="507eb-109">在提供的轉譯器之間切換</span><span class="sxs-lookup"><span data-stu-id="507eb-109">To switch between the provided renderers</span></span>  
  
- <span data-ttu-id="507eb-110">將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設定為所要的 <xref:System.Windows.Forms.ToolStripRenderMode> 值。</span><span class="sxs-lookup"><span data-stu-id="507eb-110">Set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to the <xref:System.Windows.Forms.ToolStripRenderMode> value you want.</span></span>  
  
     <span data-ttu-id="507eb-111">藉由 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>，靜態 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 決定您應用程式的轉譯器。</span><span class="sxs-lookup"><span data-stu-id="507eb-111">With <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, the static <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> determines the renderer for your application.</span></span> <span data-ttu-id="507eb-112"><xref:System.Windows.Forms.ToolStripRenderMode> 的其他值為 <xref:System.Windows.Forms.ToolStripRenderMode.Custom>、<xref:System.Windows.Forms.ToolStripRenderMode.Professional> 和 <xref:System.Windows.Forms.ToolStripRenderMode.System>。</span><span class="sxs-lookup"><span data-stu-id="507eb-112">The other values of <xref:System.Windows.Forms.ToolStripRenderMode> are <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional>, and <xref:System.Windows.Forms.ToolStripRenderMode.System>.</span></span>  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a><span data-ttu-id="507eb-113">變更 Microsoft Office 樣式框線為直線</span><span class="sxs-lookup"><span data-stu-id="507eb-113">To change the Microsoft Office–style borders to straight</span></span>  
  
- <span data-ttu-id="507eb-114">請覆寫 <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>，但不要呼叫基底類別。</span><span class="sxs-lookup"><span data-stu-id="507eb-114">Override <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, but do not call the base class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="507eb-115">該方法有用於 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 的版本。</span><span class="sxs-lookup"><span data-stu-id="507eb-115">There is a version of this method for <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer>, and <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span></span>  
  
### <a name="to-change-the-professionalcolortable"></a><span data-ttu-id="507eb-116">變更 ProfessionalColorTable</span><span class="sxs-lookup"><span data-stu-id="507eb-116">To change the ProfessionalColorTable</span></span>  
  
- <span data-ttu-id="507eb-117">覆寫 <xref:System.Windows.Forms.ProfessionalColorTable> 和變更您想要的色彩。</span><span class="sxs-lookup"><span data-stu-id="507eb-117">Override <xref:System.Windows.Forms.ProfessionalColorTable> and change the colors you want.</span></span>  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a><span data-ttu-id="507eb-118">變更您應用程式中的所有 ToolStrip 控制項轉譯</span><span class="sxs-lookup"><span data-stu-id="507eb-118">To change the rendering for all ToolStrip controls in your application</span></span>  
  
1. <span data-ttu-id="507eb-119">使用 <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> 屬性來選擇提供的轉譯器之其中一種。</span><span class="sxs-lookup"><span data-stu-id="507eb-119">Use the <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> property to choose one of the provided renderers.</span></span>  
  
2. <span data-ttu-id="507eb-120">使用 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 來指派自訂轉譯器。</span><span class="sxs-lookup"><span data-stu-id="507eb-120">Use <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> to assign a custom renderer.</span></span>  
  
3. <span data-ttu-id="507eb-121">確保 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> 的預設值。</span><span class="sxs-lookup"><span data-stu-id="507eb-121">Ensure that <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> is set to the default value of <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a><span data-ttu-id="507eb-122">關閉整個應用程式的 Microsoft Office 色彩</span><span class="sxs-lookup"><span data-stu-id="507eb-122">To turn off the Microsoft Office colors for the entire application</span></span>  
  
- <span data-ttu-id="507eb-123">請設定 <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> 為 `false`。</span><span class="sxs-lookup"><span data-stu-id="507eb-123">Set <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> to `false`.</span></span>  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a><span data-ttu-id="507eb-124">關閉 ToolStrip 控制項的 Microsoft Office 色彩</span><span class="sxs-lookup"><span data-stu-id="507eb-124">To turn off the Microsoft Office colors for one ToolStrip control</span></span>  
  
- <span data-ttu-id="507eb-125">使用與下列程式碼範例類似的程式碼。</span><span class="sxs-lookup"><span data-stu-id="507eb-125">Use code similar to the following code example.</span></span>  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="507eb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="507eb-126">See also</span></span>

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [<span data-ttu-id="507eb-127">使用內建主控描繪支援的控制項</span><span class="sxs-lookup"><span data-stu-id="507eb-127">Controls with Built-In Owner-Drawing Support</span></span>](controls-with-built-in-owner-drawing-support.md)
- [<span data-ttu-id="507eb-128">如何：建立和設定 Windows Form 中 ToolStrip 控制項自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="507eb-128">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [<span data-ttu-id="507eb-129">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="507eb-129">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
