---
title: "如何：使用 Windows Form 中的對齊線和格線排列控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: GridSize
helpviewer_keywords:
- snap to grid [Windows Forms], Windows Forms Designer
- Windows Forms, grid options in designer
- controls [Windows Forms], aligning
ms.assetid: bb54bce5-880f-4a36-af68-8cf92058dc1c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 166ccba959bd9facb8e24d580d47577a0c8746a8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-arrange-controls-with-snaplines-and-the-grid-in-windows-forms"></a><span data-ttu-id="23d5c-102">如何：使用 Windows Form 中的對齊線和格線排列控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-102">How to: Arrange Controls with Snaplines and the Grid in Windows Forms</span></span>
<span data-ttu-id="23d5c-103">使用的版面配置功能[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]，您可以精確地控制項在表單上放置的位置。</span><span class="sxs-lookup"><span data-stu-id="23d5c-103">Using the layout features of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], you can precisely direct where controls are placed on a form.</span></span> <span data-ttu-id="23d5c-104">控制項加入表單，或移到表單上自動對齊的資料列和資料行的 Windows Form 設計工具方格中，或您可以使用對齊線功能對齊控制項。</span><span class="sxs-lookup"><span data-stu-id="23d5c-104">Controls added to a form or moved on a form can be automatically aligned to the rows and columns of the Windows Forms Designer's grid, or you can align controls by using the snaplines feature.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23d5c-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="23d5c-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="23d5c-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="23d5c-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="23d5c-107">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="23d5c-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-snap-all-controls-to-the-grid"></a><span data-ttu-id="23d5c-108">貼齊至方格的所有控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-108">To snap all controls to the grid</span></span>  
  
-   <span data-ttu-id="23d5c-109">選取**SnapToGrid**在 Windows Form 設計工具的版面配置模式**選項** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23d5c-109">Select the **SnapToGrid** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="23d5c-110">如需詳細資訊，請參閱[一般]、 [Windows Form 設計工具、 [選項] 對話方塊](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)。</span><span class="sxs-lookup"><span data-stu-id="23d5c-110">For more information, see [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834).</span></span> <span data-ttu-id="23d5c-111">所有控制項現在自行都調整沿著方格上的點。</span><span class="sxs-lookup"><span data-stu-id="23d5c-111">All controls now align themselves along the points on the grid.</span></span>  
  
     <span data-ttu-id="23d5c-112">您可以鎖定在貼齊至方格的個別控制項。</span><span class="sxs-lookup"><span data-stu-id="23d5c-112">You can snap individual controls to the grid by locking them in place.</span></span> <span data-ttu-id="23d5c-113">不過，當它們被鎖定，它們無法移動或調整大小。</span><span class="sxs-lookup"><span data-stu-id="23d5c-113">However, while they are locked, they cannot be moved or resized.</span></span> <span data-ttu-id="23d5c-114">如需鎖定控制項的詳細資訊，請參閱[How to： 鎖定 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="23d5c-114">For more information about locking controls, see [How to: Lock Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-lock-controls-to-windows-forms.md).</span></span>  
  
### <a name="to-align-controls-using-snaplines"></a><span data-ttu-id="23d5c-115">使用對齊線對齊控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-115">To align controls using snaplines</span></span>  
  
-   <span data-ttu-id="23d5c-116">選取**對齊線**在 Windows Form 設計工具的版面配置模式**選項** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23d5c-116">Select the **SnapLines** layout mode in the Windows Forms Designer **Options** dialog box.</span></span>  
  
     <span data-ttu-id="23d5c-117">如需詳細資訊，請參閱[逐步解說： 在 Windows Form 使用對齊線排列的控制項](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)。</span><span class="sxs-lookup"><span data-stu-id="23d5c-117">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span> <span data-ttu-id="23d5c-118">您現在可以使用對齊線對齊及排列表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="23d5c-118">You can now use snaplines to align and arrange controls on your form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d5c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="23d5c-119">See Also</span></span>  
 [<span data-ttu-id="23d5c-120">選項對話方塊、 Windows Form 設計工具，一般</span><span class="sxs-lookup"><span data-stu-id="23d5c-120">General, Windows Forms Designer, Options Dialog Box</span></span>](http://msdn.microsoft.com/library/8dd170af-72f0-4212-b04b-034ceee92834)  
 [<span data-ttu-id="23d5c-121">逐步解說：使用對齊線排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-121">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="23d5c-122">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-122">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="23d5c-123">操作說明：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23d5c-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="23d5c-124">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-124">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="23d5c-125">標記個別 Windows Forms 控制項並提供其捷徑</span><span class="sxs-lookup"><span data-stu-id="23d5c-125">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="23d5c-126">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-126">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="23d5c-127">依功能區分 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="23d5c-127">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
