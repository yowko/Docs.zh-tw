---
title: 作法：在 [選擇工具箱項目] 對話方塊中顯示控制項
ms.date: 03/30/2017
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a6938b4fe651e13f3ec96642db6027143f1f028
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015887"
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="540fe-102">HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項</span><span class="sxs-lookup"><span data-stu-id="540fe-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>

<span data-ttu-id="540fe-103">當您開發和散發控制項時, 您可能會想要讓這些控制項出現在 Visual Studio 的 [**選擇工具箱專案**] 對話方塊中, 當您以滑鼠右鍵按一下 [**工具箱**] 並選取 **[選擇專案**] 時, 就會顯示此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="540fe-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box of Visual Studio, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="540fe-104">您可以使用 AssemblyFoldersEx 註冊程式, 讓控制項出現在此對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="540fe-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>

<span data-ttu-id="540fe-105">若要在 [選擇工具箱專案] 對話方塊中顯示控制項:</span><span class="sxs-lookup"><span data-stu-id="540fe-105">To display your control in the Choose Toolbox Items dialog box:</span></span>

- <span data-ttu-id="540fe-106">將您的控制群組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="540fe-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="540fe-107">如需詳細資訊，請參閱[如何：在全域組件快取中安裝單一組件](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="540fe-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>

  <span data-ttu-id="540fe-108">-或-</span><span class="sxs-lookup"><span data-stu-id="540fe-108">-or-</span></span>

- <span data-ttu-id="540fe-109">使用 AssemblyFoldersEx 註冊程式, 註冊您的控制項及其相關聯的設計階段元件。</span><span class="sxs-lookup"><span data-stu-id="540fe-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="540fe-110">AssemblyFoldersEx 是一個登錄位置, 其中協力廠商會儲存其所支援的每個架構版本的路徑。</span><span class="sxs-lookup"><span data-stu-id="540fe-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="540fe-111">設計階段解決方案可以在此登錄位置尋找參考元件。</span><span class="sxs-lookup"><span data-stu-id="540fe-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="540fe-112">登入指令檔可指定您想要在 [工具箱] 中顯示的控制項。</span><span class="sxs-lookup"><span data-stu-id="540fe-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="540fe-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="540fe-113">See also</span></span>

- [<span data-ttu-id="540fe-114">在設計階段開發 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="540fe-114">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="540fe-115">如何：在全域組件快取中安裝單一組件</span><span class="sxs-lookup"><span data-stu-id="540fe-115">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../app-domains/how-to-install-an-assembly-into-the-gac.md)
- [<span data-ttu-id="540fe-116">逐步解說：使用自訂群組件自動填入工具箱</span><span class="sxs-lookup"><span data-stu-id="540fe-116">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
