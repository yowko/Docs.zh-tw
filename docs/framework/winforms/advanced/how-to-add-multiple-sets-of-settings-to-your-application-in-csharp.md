---
title: 如何：在 C# 中將多組設定新增至應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040131"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="9f980-102">如何：在 C 中將多組設定新增至您的應用程式\#</span><span class="sxs-lookup"><span data-stu-id="9f980-102">How To: Add Multiple Sets of Settings To Your Application in C\#</span></span>

<span data-ttu-id="9f980-103">在某些情況下, 您可能會想要在應用程式中有多組設定。</span><span class="sxs-lookup"><span data-stu-id="9f980-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="9f980-104">例如, 如果您正在開發一個應用程式, 其中特定的設定群組預期會經常變更, 則將它們全部分隔成單一檔案可能會很明智, 如此一來, 就可以將檔案替換成批發, 讓其他設定不受影響。</span><span class="sxs-lookup"><span data-stu-id="9f980-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="9f980-105">Visual Studio 可讓您將多組設定加入至專案。</span><span class="sxs-lookup"><span data-stu-id="9f980-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="9f980-106">您可以透過`Properties.Settings`物件存取額外的設定集合。</span><span class="sxs-lookup"><span data-stu-id="9f980-106">Additional sets of settings can be accessed via the `Properties.Settings` object.</span></span>

## <a name="add-an-additional-set-of-settings"></a><span data-ttu-id="9f980-107">新增一組額外的設定</span><span class="sxs-lookup"><span data-stu-id="9f980-107">Add an Additional Set of Settings</span></span>

1. <span data-ttu-id="9f980-108">在 Visual Studio 中, 從 [**專案**] 功能表選擇 [**加入新專案**]。</span><span class="sxs-lookup"><span data-stu-id="9f980-108">In Visual Studio, from the **Project** menu, choose **Add New Item**.</span></span>

   <span data-ttu-id="9f980-109">[新增項目] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="9f980-109">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="9f980-110">在 [**加入新專案**] 對話方塊中, 選取 [**設定檔**], 輸入檔案的名稱, 然後按一下 [**新增**] 將新的設定檔新增至您的方案。</span><span class="sxs-lookup"><span data-stu-id="9f980-110">In the **Add New Item** dialog box, select **Settings File**, enter a name for the file, and click **Add** to add a new settings file to your solution.</span></span>

3. <span data-ttu-id="9f980-111">在**方案總管**中, 將新的設定檔案拖曳至 [ **Properties** ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f980-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="9f980-112">這可讓您在程式碼中使用新的設定。</span><span class="sxs-lookup"><span data-stu-id="9f980-112">This allows your new settings to be available in code.</span></span>

4. <span data-ttu-id="9f980-113">新增和使用此檔案中的設定, 就像任何其他設定檔一樣。</span><span class="sxs-lookup"><span data-stu-id="9f980-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="9f980-114">您可以透過`Properties.Settings`物件存取這組設定。</span><span class="sxs-lookup"><span data-stu-id="9f980-114">You can access this group of settings via the `Properties.Settings` object.</span></span>

## <a name="see-also"></a><span data-ttu-id="9f980-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f980-115">See also</span></span>

- [<span data-ttu-id="9f980-116">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="9f980-116">Using Application Settings and User Settings</span></span>](using-application-settings-and-user-settings.md)
- [<span data-ttu-id="9f980-117">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="9f980-117">Application Settings Overview</span></span>](application-settings-overview.md)
