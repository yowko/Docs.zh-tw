---
title: "如何：將組件安裝到全域組件快取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98dd4d1e75fc37820a1b1f4eccfa48f978772687
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="4303c-102">如何：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="4303c-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="4303c-103">有兩種方式可以將強式名稱組件安裝到全域組件快取 (GAC) 中：</span><span class="sxs-lookup"><span data-stu-id="4303c-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4303c-104">只有強式名稱組件才能安裝至 GAC。</span><span class="sxs-lookup"><span data-stu-id="4303c-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="4303c-105">如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="4303c-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="4303c-106">使用 [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4303c-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="4303c-107">在 Visual Studio 2012 和 Visual Studio 2013 中可以透過建立 InstallShield Limited Edition 專案的方式達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="4303c-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="4303c-108">建議您使用這個新增組件到全域組件快取，這是最常用的方法。</span><span class="sxs-lookup"><span data-stu-id="4303c-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="4303c-109">安裝程式會提供全域組件快取的組件參考計數，以及其他功能。</span><span class="sxs-lookup"><span data-stu-id="4303c-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="4303c-110">使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="4303c-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="4303c-111">您可以使用 Gacutil.exe 將強式名稱的組件新增到全域組件快取，和檢視全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="4303c-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4303c-112">Gacutil.exe 僅適合開發用途，不應用來安裝產品組件到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4303c-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4303c-113">在舊版 .NET Framework 中，可利用 Shfusion.dll Windows Shell Extension 將組件拖曳到 [檔案總管] 中，藉此安裝組件。</span><span class="sxs-lookup"><span data-stu-id="4303c-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="4303c-114">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，Shfusion.dll 已過時。</span><span class="sxs-lookup"><span data-stu-id="4303c-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="4303c-115">若要使用全域組件快取工具 (Gacutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4303c-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="4303c-116">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4303c-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="4303c-117">**gacutil -i** \<組件名稱></span><span class="sxs-lookup"><span data-stu-id="4303c-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="4303c-118">在這個命令中，「組件名稱」是安裝在全域組件快取的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="4303c-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="4303c-119">下列範例安裝檔名為 `hello.dll` 的組件到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4303c-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="4303c-120">如需詳細資訊，請參閱[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="4303c-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="4303c-121">若要使用 InstallShield Limited Edition 專案</span><span class="sxs-lookup"><span data-stu-id="4303c-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="4303c-122">開啟方案的捷徑功能表，然後依序選擇 [新增] 和 [新專案]，以將安裝和部署套件新增至方案。</span><span class="sxs-lookup"><span data-stu-id="4303c-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="4303c-123">在 [新增專案] 對話方塊中，於 [已安裝] 資料夾中選擇 [其他專案類型]、[安裝和部署]、[InstallShield Limited Edition]，然後為您的專案命名。</span><span class="sxs-lookup"><span data-stu-id="4303c-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="4303c-124">(出現提示時，下載、安裝並啟動 InstallShield。)</span><span class="sxs-lookup"><span data-stu-id="4303c-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="4303c-125">使用方案總管中的 [專案助理]，或是選擇方案總管中編號步驟的子步驟，執行安裝和部署專案的一般組態。設定您的安裝程式，就像未將組件新增至 GAC 一樣。</span><span class="sxs-lookup"><span data-stu-id="4303c-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="4303c-126">若要開始將組件新增至 GAC 的程序，請選擇位於方案總管的 [指定應用程式資料] 步驟下的 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="4303c-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="4303c-127">在 [目的電腦的資料夾] 窗格中，開啟 [目的電腦] 的捷徑功能表，然後選擇 [顯示預先定義的資料夾]和 [[GlobalAssemblyCache]]。</span><span class="sxs-lookup"><span data-stu-id="4303c-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="4303c-128">對於方案中包含您要在全域組件快取中安裝之組件的每個專案：</span><span class="sxs-lookup"><span data-stu-id="4303c-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="4303c-129">在 [來源電腦的資料夾] 窗格中，選擇專案。</span><span class="sxs-lookup"><span data-stu-id="4303c-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="4303c-130">在 [目的電腦的資料夾] 窗格中，選擇 [[GlobalAssemblyCache]]。</span><span class="sxs-lookup"><span data-stu-id="4303c-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="4303c-131">在 [來源電腦的檔案] 窗格中，選擇 [主要輸出來自 *<project_name>*]。</span><span class="sxs-lookup"><span data-stu-id="4303c-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="4303c-132">將步驟 c 中的檔案拖曳至 [目的電腦的檔案] 窗格中 (或使用檔案的捷徑功能表上的 [複製] 和 [貼上] 命令)。</span><span class="sxs-lookup"><span data-stu-id="4303c-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4303c-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="4303c-133">See Also</span></span>  
 [<span data-ttu-id="4303c-134">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="4303c-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="4303c-135">操作說明：從全域組件快取移除組件</span><span class="sxs-lookup"><span data-stu-id="4303c-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="4303c-136">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="4303c-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="4303c-137">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="4303c-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="4303c-138">Windows Installer 部署</span><span class="sxs-lookup"><span data-stu-id="4303c-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
