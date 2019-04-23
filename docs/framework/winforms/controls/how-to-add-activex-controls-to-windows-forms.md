---
title: HOW TO：將 ActiveX 控制項新增至 Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 780411949c543a2178de5e7c531bd2202703f27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166045"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="24dee-102">HOW TO：將 ActiveX 控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24dee-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="24dee-103">雖然 Windows Forms 設計工具已最佳化來裝載 Windows Forms 控制項中，您也可以使 Windows Form 上的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="24dee-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="24dee-104">ActiveX 控制項新增至它們時，則需要有 Windows Forms 的效能限制。</span><span class="sxs-lookup"><span data-stu-id="24dee-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="24dee-105">您將 ActiveX 控制項新增至您的表單之前，您必須將它們加入 [工具箱] 中。</span><span class="sxs-lookup"><span data-stu-id="24dee-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="24dee-106">如需詳細資訊，請參閱 < [COM 元件、 自訂工具箱對話方塊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="24dee-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24dee-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="24dee-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="24dee-108">若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="24dee-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="24dee-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="24dee-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="24dee-110">將 ActiveX 控制項新增至您的 Windows 表單</span><span class="sxs-lookup"><span data-stu-id="24dee-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="24dee-111">按兩下 [工具箱] 控制項。</span><span class="sxs-lookup"><span data-stu-id="24dee-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="24dee-112">Visual Studio 專案中新增至控制項的所有參考。</span><span class="sxs-lookup"><span data-stu-id="24dee-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="24dee-113">如需有關使用 Windows Form 上的 ActiveX 控制項時，請記住的事項的詳細資訊，請參閱[裝載在 Windows Form 上的 ActiveX 控制項的考慮因素](considerations-when-hosting-an-activex-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="24dee-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24dee-114">非預期的 ActiveX 動態連結程式庫匯入作業時，Windows Forms ActiveX 控制項匯入工具 (AxImp.exe) 就會建立不同類型的事件引數。</span><span class="sxs-lookup"><span data-stu-id="24dee-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="24dee-115">AxImp.exe 所建立的引數會與下列類似： `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`，當`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`預期。</span><span class="sxs-lookup"><span data-stu-id="24dee-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="24dee-116">請注意，此種不規則變化不會防止程式碼正常運作。</span><span class="sxs-lookup"><span data-stu-id="24dee-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="24dee-117">如需詳細資訊，請參閱 < [Windows Forms ActiveX 控制項匯入工具 (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="24dee-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24dee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24dee-118">See also</span></span>

- [<span data-ttu-id="24dee-119">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="24dee-119">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="24dee-120">[比較各種語言和程式庫的控制項與可以透過程式設計的物件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="24dee-120">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="24dee-121">如何：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24dee-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="24dee-122">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="24dee-122">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="24dee-123">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="24dee-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="24dee-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="24dee-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="24dee-125">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="24dee-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
