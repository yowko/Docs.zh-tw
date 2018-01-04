---
title: "如何：在選擇工具箱項目對話方塊中顯示控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1323ffbd59a14d19d1161e0718fad083bcc37a89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="6f9db-102">如何：在選擇工具箱項目對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="6f9db-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="6f9db-103">當您開發並散發控制項，您可能會想要出現在這些控制項**選擇工具箱項目**對話方塊中，當您以滑鼠右鍵按一下顯示**工具箱**選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="6f9db-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="6f9db-104">您可以啟用您的控制項才會出現在這個對話方塊中，使用 AssemblyFoldersEx 登錄程序。</span><span class="sxs-lookup"><span data-stu-id="6f9db-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="6f9db-105">在 [選擇工具箱項目] 對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="6f9db-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="6f9db-106">控制項組件安裝至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="6f9db-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="6f9db-107">如需詳細資訊，請參閱[How to： 將組件安裝到全域組件快取](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="6f9db-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="6f9db-108">-或-</span><span class="sxs-lookup"><span data-stu-id="6f9db-108">-or-</span></span>  
  
-   <span data-ttu-id="6f9db-109">註冊您的控制項和其相關聯的設計階段組件使用 AssemblyFoldersEx 登錄程序。</span><span class="sxs-lookup"><span data-stu-id="6f9db-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="6f9db-110">AssemblyFoldersEx 是協力廠商儲存每個版本的 framework 所支援路徑的登錄位置。</span><span class="sxs-lookup"><span data-stu-id="6f9db-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="6f9db-111">設計階段解析度可以查看此登錄位置中尋找參考組件中。</span><span class="sxs-lookup"><span data-stu-id="6f9db-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="6f9db-112">登錄指令碼可以指定您想要出現在工具箱中的控制項。</span><span class="sxs-lookup"><span data-stu-id="6f9db-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="6f9db-113">如需詳細資訊，請參閱[部署自訂控制項和設計階段組件 (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)。</span><span class="sxs-lookup"><span data-stu-id="6f9db-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9db-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f9db-114">See Also</span></span>  
 [<span data-ttu-id="6f9db-115">選擇工具箱項目對話方塊 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="6f9db-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="6f9db-116">部署自訂控制項和設計階段組件 (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="6f9db-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="6f9db-117">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="6f9db-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="6f9db-118">操作說明：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="6f9db-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="6f9db-119">逐步解說：自動將自訂元件填入工具箱</span><span class="sxs-lookup"><span data-stu-id="6f9db-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
