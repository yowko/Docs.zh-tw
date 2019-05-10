---
title: HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
ms.openlocfilehash: 4ed3f6ffdf8a86d050b81311c9211767d8b179b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623604"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="fa6ba-102">HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="fa6ba-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="fa6ba-103">當您開發並散發控制項時，您可能需要才會出現在這些控制項**選擇工具箱項目** 對話方塊中，當您以滑鼠右鍵按一下顯示**工具箱**，然後選取**選擇項目**。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="fa6ba-104">您可以讓您的控制項才會出現在這個對話方塊中，使用 AssemblyFoldersEx 登錄程序。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="fa6ba-105">在 [選擇工具箱項目] 對話方塊中顯示您的控制項</span><span class="sxs-lookup"><span data-stu-id="fa6ba-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
- <span data-ttu-id="fa6ba-106">您的控制項組件安裝至全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="fa6ba-107">如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="fa6ba-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="fa6ba-108">-或-</span><span class="sxs-lookup"><span data-stu-id="fa6ba-108">-or-</span></span>  
  
- <span data-ttu-id="fa6ba-109">使用 AssemblyFoldersEx 登錄程序中註冊您的控制項和其相關聯的設計階段組件。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="fa6ba-110">AssemblyFoldersEx 是 framework 的第三方廠商在其中儲存每個支援版本的路徑的登錄位置。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="fa6ba-111">設計階段解析度可以查看此登錄位置中找到參考組件。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="fa6ba-112">登錄指令碼可以指定您想要出現在工具箱中的控制項。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="fa6ba-113">如需詳細資訊，請參閱 <<c0> [ 部署自訂控制項和設計階段組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="fa6ba-113">For more information, see [Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6ba-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa6ba-114">See also</span></span>

- <span data-ttu-id="fa6ba-115">[選擇工具箱項目對話方塊 (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fa6ba-115">[Choose Toolbox Items Dialog Box (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))</span></span>
- <span data-ttu-id="fa6ba-116">[部署自訂控制項和設計階段組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fa6ba-116">[Deploying a Custom Control and Design-time Assemblies](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee849818(v=vs.100))</span></span>
- [<span data-ttu-id="fa6ba-117">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="fa6ba-117">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="fa6ba-118">如何：在全域組件快取中安裝單一組件</span><span class="sxs-lookup"><span data-stu-id="fa6ba-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- <span data-ttu-id="fa6ba-119">[逐步解說：自動填入 [工具箱] 中的以自訂元件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="fa6ba-119">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>
