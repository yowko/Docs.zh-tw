---
title: 如何：在設計階段複製和貼上 ElementHost 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3d1887eb1161f714962c2c26d6fe618749b26c0f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197473"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="2a373-102">如何：複製和貼上 ElementHost 控制項</span><span class="sxs-lookup"><span data-stu-id="2a373-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="2a373-103">此程式說明如何在 Visual Studio 中複製 Windows Form 上的 Windows Presentation Foundation （WPF）控制項。</span><span class="sxs-lookup"><span data-stu-id="2a373-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="2a373-104">在 Visual Studio 中，將新的 WPF <xref:System.Windows.Controls.UserControl> 加入至 Windows Forms 專案。</span><span class="sxs-lookup"><span data-stu-id="2a373-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="2a373-105">使用控制項類型的預設名稱 `UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="2a373-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="2a373-106">如需詳細資訊，請參閱[逐步解說：在設計階段于 Windows Forms 上建立新的 WPF 內容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="2a373-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="2a373-107">在 [**屬性**] 視窗中，將 `UserControl1` 的 [<xref:System.Windows.FrameworkElement.Width%2A>] 和 [<xref:System.Windows.FrameworkElement.Height%2A> 屬性] 的值設定為**200**。</span><span class="sxs-lookup"><span data-stu-id="2a373-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="2a373-108">將 [<xref:System.Windows.Controls.Control.Background%2A>] 屬性的值設定為 [**藍色**]。</span><span class="sxs-lookup"><span data-stu-id="2a373-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="2a373-109">建置專案。</span><span class="sxs-lookup"><span data-stu-id="2a373-109">Build the project.</span></span>

5. <span data-ttu-id="2a373-110">在 Windows Form 設計工具中開啟 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="2a373-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="2a373-111">從 [**工具箱**] 中，將 `UserControl1` 的實例拖曳至表單上。</span><span class="sxs-lookup"><span data-stu-id="2a373-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="2a373-112">`UserControl1` 的執行個體裝載於名為 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="2a373-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="2a373-113">選取 `elementHost1` 後，請按**Ctrl**+**C** ，將它複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="2a373-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="2a373-114">按**Ctrl**+**V** ，將複製的控制項貼入表單上。</span><span class="sxs-lookup"><span data-stu-id="2a373-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="2a373-115">會在表單上建立名為 `elementHost2` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控制項。</span><span class="sxs-lookup"><span data-stu-id="2a373-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a373-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a373-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="2a373-117">移轉和互通性</span><span class="sxs-lookup"><span data-stu-id="2a373-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="2a373-118">使用 WPF 控制項</span><span class="sxs-lookup"><span data-stu-id="2a373-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="2a373-119">在 Visual Studio 中設計 XAML</span><span class="sxs-lookup"><span data-stu-id="2a373-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
