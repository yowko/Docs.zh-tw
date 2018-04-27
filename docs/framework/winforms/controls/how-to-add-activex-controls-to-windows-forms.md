---
title: 如何：將 ActiveX 控制項加入至 Windows Form
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2cedd71665dc098ca3a6a6bf43c74b2d3a11fe11
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="e51d5-102">如何：將 ActiveX 控制項加入至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="e51d5-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="e51d5-103">Windows Form 設計工具最適合主機的 Windows Form 控制項，而您也可以使 Windows Form 上的 ActiveX 控制項。</span><span class="sxs-lookup"><span data-stu-id="e51d5-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e51d5-104">ActiveX 控制項新增到它們時，有適用於 Windows Form 的效能限制。</span><span class="sxs-lookup"><span data-stu-id="e51d5-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="e51d5-105">您將 ActiveX 控制項加入至表單之前，您必須將他們加入 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="e51d5-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="e51d5-106">如需詳細資訊，請參閱[COM 元件、 自訂工具箱對話方塊](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c)。</span><span class="sxs-lookup"><span data-stu-id="e51d5-106">For more information, see [COM Components, Customize Toolbox Dialog Box](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e51d5-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="e51d5-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="e51d5-108">若要變更設定，請在 [工具]  功能表上按一下 [匯入和匯出設定]  。</span><span class="sxs-lookup"><span data-stu-id="e51d5-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="e51d5-109">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="e51d5-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="e51d5-110">若要將 ActiveX 控制項加入至您的 Windows Form</span><span class="sxs-lookup"><span data-stu-id="e51d5-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="e51d5-111">按兩下 [工具箱] 控制項。</span><span class="sxs-lookup"><span data-stu-id="e51d5-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="e51d5-112">Visual Studio 專案中加入控制項的所有參考。</span><span class="sxs-lookup"><span data-stu-id="e51d5-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="e51d5-113">如需使用 Windows Form 上的 ActiveX 控制項時，請記住的事項的詳細資訊，請參閱[裝載 Windows Form 上的 ActiveX 控制項時的考量](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="e51d5-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e51d5-114">Windows Form ActiveX 控制項匯入工具 (AxImp.exe) 超過預期的 ActiveX 動態連結程式庫匯入作業時，會建立不同類型的事件引數。</span><span class="sxs-lookup"><span data-stu-id="e51d5-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="e51d5-115">AxImp.exe 所建立的引數都與下列類似： `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`，當`Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)`預期。</span><span class="sxs-lookup"><span data-stu-id="e51d5-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="e51d5-116">請注意，此不規則不會阻止程式碼正常運作。</span><span class="sxs-lookup"><span data-stu-id="e51d5-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="e51d5-117">如需詳細資訊，請參閱[Windows Form ActiveX 控制項匯入工具 (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)。</span><span class="sxs-lookup"><span data-stu-id="e51d5-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51d5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e51d5-118">See Also</span></span>  
 [<span data-ttu-id="e51d5-119">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e51d5-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="e51d5-120">比較各種語言和程式庫的控制項與可以透過程式設計的物件</span><span class="sxs-lookup"><span data-stu-id="e51d5-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="e51d5-121">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e51d5-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="e51d5-122">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="e51d5-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="e51d5-123">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="e51d5-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="e51d5-124">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="e51d5-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="e51d5-125">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="e51d5-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
