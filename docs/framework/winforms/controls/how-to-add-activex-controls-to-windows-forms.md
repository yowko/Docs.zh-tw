---
title: 如何：將 ActiveX 控制項加入至 Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 7d6514c679187e9ec193f6dda8336c8bd56fac81
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705397"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="46b5b-102">如何：將 ActiveX 控制項加入至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="46b5b-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="46b5b-103">雖然 Windows Forms 設計工具已最佳化來裝載 Windows Forms 控制項中，您也可以使 Windows Form 上的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="46b5b-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="46b5b-104">ActiveX 控制項新增至它們時，則需要有 Windows Forms 的效能限制。</span><span class="sxs-lookup"><span data-stu-id="46b5b-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="46b5b-105">您將 ActiveX 控制項新增至您的表單之前，您必須將它們加入 [工具箱] 中。</span><span class="sxs-lookup"><span data-stu-id="46b5b-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="46b5b-106">如需詳細資訊，請參閱 < [COM 元件、 自訂工具箱對話方塊](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c)。</span><span class="sxs-lookup"><span data-stu-id="46b5b-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46b5b-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="46b5b-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="46b5b-108">若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="46b5b-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="46b5b-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="46b5b-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="46b5b-110">將 ActiveX 控制項新增至您的 Windows 表單</span><span class="sxs-lookup"><span data-stu-id="46b5b-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="46b5b-111">按兩下 [工具箱] 控制項。</span><span class="sxs-lookup"><span data-stu-id="46b5b-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="46b5b-112">Visual Studio 專案中新增至控制項的所有參考。</span><span class="sxs-lookup"><span data-stu-id="46b5b-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="46b5b-113">如需有關使用 Windows Form 上的 ActiveX 控制項時，請記住的事項的詳細資訊，請參閱[裝載在 Windows Form 上的 ActiveX 控制項的考慮因素](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="46b5b-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="46b5b-114">非預期的 ActiveX 動態連結程式庫匯入作業時，Windows Forms ActiveX 控制項匯入工具 (AxImp.exe) 就會建立不同類型的事件引數。</span><span class="sxs-lookup"><span data-stu-id="46b5b-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="46b5b-115">AxImp.exe 所建立的引數會與下列類似： `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`，當`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`預期。</span><span class="sxs-lookup"><span data-stu-id="46b5b-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="46b5b-116">請注意，此種不規則變化不會防止程式碼正常運作。</span><span class="sxs-lookup"><span data-stu-id="46b5b-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="46b5b-117">如需詳細資訊，請參閱 < [Windows Forms ActiveX 控制項匯入工具 (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="46b5b-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46b5b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46b5b-118">See Also</span></span>  
 [<span data-ttu-id="46b5b-119">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="46b5b-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="46b5b-120">比較各種語言和程式庫的控制項與可以透過程式設計的物件</span><span class="sxs-lookup"><span data-stu-id="46b5b-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="46b5b-121">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46b5b-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="46b5b-122">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="46b5b-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="46b5b-123">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="46b5b-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="46b5b-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="46b5b-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="46b5b-125">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="46b5b-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
