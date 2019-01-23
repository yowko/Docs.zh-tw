---
title: 如何：將多組設定新增至您的應用程式C#
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 5496d370890e019ae2b31835c95a9988f8d9bc18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559407"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="706ae-102">如何：將多組設定新增至您的應用程式C#</span><span class="sxs-lookup"><span data-stu-id="706ae-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="706ae-103">在某些情況下，您可能想要的應用程式中有多組設定。</span><span class="sxs-lookup"><span data-stu-id="706ae-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="706ae-104">比方說，如果您正在開發應用程式特定群組的設定應該在其中經常變更，它可能是個明智的選擇，讓檔案可以全面，取代成單一檔案的所有分隔它們保留其他設定不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="706ae-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="706ae-105">Visual Studio 可讓您將多組設定新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="706ae-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="706ae-106">可透過 Properties.Settings 物件存取設定的其他集合。</span><span class="sxs-lookup"><span data-stu-id="706ae-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="706ae-107">若要將一組額外的設定新增至您的應用程式</span><span class="sxs-lookup"><span data-stu-id="706ae-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="706ae-108">從 [專案] 功能表選擇 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="706ae-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="706ae-109">[新增項目] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="706ae-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="706ae-110">在 **加入新項目**對話方塊中，選取**設定檔**，輸入檔案名稱，然後按一下**新增**將新的設定檔新增至您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="706ae-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="706ae-111">在 **方案總管**，將拖曳至新的設定檔**屬性**資料夾。</span><span class="sxs-lookup"><span data-stu-id="706ae-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="706ae-112">這可讓您可在程式碼中使用的新設定。</span><span class="sxs-lookup"><span data-stu-id="706ae-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="706ae-113">新增並使用此檔案中的設定，就如同任何其他的設定檔。</span><span class="sxs-lookup"><span data-stu-id="706ae-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="706ae-114">您可以存取此設定，透過 Properties.Settings 物件群組。</span><span class="sxs-lookup"><span data-stu-id="706ae-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706ae-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="706ae-115">See also</span></span>
- [<span data-ttu-id="706ae-116">使用應用程式設定和使用者設定</span><span class="sxs-lookup"><span data-stu-id="706ae-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [<span data-ttu-id="706ae-117">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="706ae-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
