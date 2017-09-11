---
title: "如何：判斷安裝的 .NET Framework 更新"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b29b402e859688dcced6bd4429b18298070fb5e4
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="1e34b-102">如何：判斷安裝的 .NET Framework 更新</span><span class="sxs-lookup"><span data-stu-id="1e34b-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="1e34b-103">電腦上所安裝之每一版 .NET Framework 已安裝的更新都會列在 Windows 登錄中。</span><span class="sxs-lookup"><span data-stu-id="1e34b-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="1e34b-104">您可以使用登錄編輯程式 (regedit.exe) 檢視這項資訊。</span><span class="sxs-lookup"><span data-stu-id="1e34b-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="1e34b-105">在登錄編輯程式中，.NET Framework 版本和每一版已安裝的更新會儲存在不同的子機碼中。</span><span class="sxs-lookup"><span data-stu-id="1e34b-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="1e34b-106">如需偵測已安裝之版本號碼的相關資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。</span><span class="sxs-lookup"><span data-stu-id="1e34b-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="1e34b-107">如需安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="1e34b-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="1e34b-108">尋找已安裝的更新</span><span class="sxs-lookup"><span data-stu-id="1e34b-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="1e34b-109">開啟 **regedit.exe** 程式。</span><span class="sxs-lookup"><span data-stu-id="1e34b-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="1e34b-110">在 Windows 8 (含) 以上版本中，開啟 [開始] 畫面，然後輸入名稱。</span><span class="sxs-lookup"><span data-stu-id="1e34b-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="1e34b-111">在舊版 Windows 中，於 [開始] 功能表上選擇 [執行]，然後在 [開啟] 方塊中輸入 **regedit.exe**。</span><span class="sxs-lookup"><span data-stu-id="1e34b-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="1e34b-112">您必須具有系統管理認證才能執行 regedit.exe。</span><span class="sxs-lookup"><span data-stu-id="1e34b-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="1e34b-113">在 [登錄編輯程式] 中，開啟下列子機碼：</span><span class="sxs-lookup"><span data-stu-id="1e34b-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="1e34b-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="1e34b-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="1e34b-115">已安裝的更新會列於子機碼下，這些子機碼可識別套用更新的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="1e34b-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="1e34b-116">每個更新都是透過知識庫 (KB) 號碼加以識別。</span><span class="sxs-lookup"><span data-stu-id="1e34b-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e34b-117">範例</span><span class="sxs-lookup"><span data-stu-id="1e34b-117">Example</span></span>  
 <span data-ttu-id="1e34b-118">下列程式碼以程式設計方式判斷電腦上所安裝的 .NET Framework 更新。</span><span class="sxs-lookup"><span data-stu-id="1e34b-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="1e34b-119">您必須具有系統管理認證才能執行這個範例。</span><span class="sxs-lookup"><span data-stu-id="1e34b-119">You must have administrative credentials to run this example.</span></span>  
  
 <span data-ttu-id="1e34b-120">[!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="1e34b-120">[!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]</span></span>  
  
 <span data-ttu-id="1e34b-121">這個範例產生的輸出類似下面所述：</span><span class="sxs-lookup"><span data-stu-id="1e34b-121">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e34b-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="1e34b-122">See also</span></span>

<span data-ttu-id="1e34b-123">[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="1e34b-123">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="1e34b-124">[安裝 .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="1e34b-124">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="1e34b-125">版本和相依性</span><span class="sxs-lookup"><span data-stu-id="1e34b-125">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)

