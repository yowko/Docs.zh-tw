---
title: "針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a><span data-ttu-id="5c695-102">針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案</span><span class="sxs-lookup"><span data-stu-id="5c695-102">Writing Projects Targeting the .NET Framework 3.0 and 3.5 in Visual Studio 2010</span></span>
<span data-ttu-id="5c695-103">您可以使用 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 來建立以 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 3.0 或 3.5 版為目標的專案。</span><span class="sxs-lookup"><span data-stu-id="5c695-103">You can use [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] to create projects that target the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 or 3.5.</span></span> <span data-ttu-id="5c695-104">本主題描述如何執行這個工作。</span><span class="sxs-lookup"><span data-stu-id="5c695-104">This topic describes how to do this.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c695-105">當加入活動時，請務必設定所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="5c695-105">When adding activities, make sure that the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] is set.</span></span> <span data-ttu-id="5c695-106">在加入活動之後變更工作流程的目標版本將會導致工作流程驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="5c695-106">Changing the target version of the workflow after activities are added will cause the workflow to fail validation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="5c695-107">在 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 中開啟擁有 .Net Framework 3.5 活動的現有工作流程將會導致 `this.SetValue()` 發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5c695-107">Opening existing workflows in [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] that have .Net Framework 3.5 activities will cause an error at `this.SetValue()`.</span></span> <span data-ttu-id="5c695-108">為了開啟之前使用舊版 .Net Framework 所建立的專案，請先在設計工具中開啟空白工作流程，然後加入 .Net Framework 3.5 活動。</span><span class="sxs-lookup"><span data-stu-id="5c695-108">In order to open projects created with previous versions of the .Net Framework, first open a blank workflow in the designer and add a .Net Framework 3.5 activity.</span></span>  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a><span data-ttu-id="5c695-109">若要使用 Visual Studio 2010 建立 .NET Framework 3.0 或 3.5 專案</span><span class="sxs-lookup"><span data-stu-id="5c695-109">To create a .NET Framework  3.0 or 3.5 project with Visual Studio 2010</span></span>  
  
1.  <span data-ttu-id="5c695-110">開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5c695-110">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5c695-111">選取**檔案**，**新**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="5c695-111">Select **File**, **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="5c695-112">在對話方塊上方的下拉式清單中，選取所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="5c695-112">In the drop-down list at the top of the dialog box, select the desired version of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a><span data-ttu-id="5c695-113">若要升級 .NET Framework 的目標版本</span><span class="sxs-lookup"><span data-stu-id="5c695-113">To upgrade the targeted version of the .NET Framework</span></span>  
  
1.  <span data-ttu-id="5c695-114">以滑鼠右鍵按一下方案總管 中的專案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5c695-114">Right-click the project in Solution Explorer, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="5c695-115">在**目標 Framework**下拉式清單中，選取所需的版本。</span><span class="sxs-lookup"><span data-stu-id="5c695-115">In the **Target Framework** drop-down list, select the desired version.</span></span>
