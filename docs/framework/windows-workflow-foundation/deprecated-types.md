---
title: "Windows Workflow Foundation 中被取代的類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 422e95a105978749cc56dfe6601fb4518cc11509
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="1fd78-102">Windows Workflow Foundation 中被取代的類型</span><span class="sxs-lookup"><span data-stu-id="1fd78-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="1fd78-103">在 .NET 4 中，工作流程小組在 <xref:System.Activities> 命名空間中發行了全新的工作流程引擎。</span><span class="sxs-lookup"><span data-stu-id="1fd78-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="1fd78-104">.NET 4.5 Beta 版本中，我們要標記的大部分"WF 3"中類型<xref:System.Workflow.Activities>， <xref:System.Workflow.ComponentModel>，和<xref:System.Workflow.Runtime>命名空間為已過時。</span><span class="sxs-lookup"><span data-stu-id="1fd78-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="1fd78-105">過時的命名空間和工具</span><span class="sxs-lookup"><span data-stu-id="1fd78-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="1fd78-106">下列組件含有一個或多個將會被取代的公用型別：</span><span class="sxs-lookup"><span data-stu-id="1fd78-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
-   <span data-ttu-id="1fd78-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="1fd78-107">System.Workflow.Activities.dll</span></span>  
  
-   <span data-ttu-id="1fd78-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="1fd78-108">System.Workflow.ComponentModel.dll</span></span>  
  
-   <span data-ttu-id="1fd78-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="1fd78-109">System.Workflow.Runtime.dll</span></span>  
  
-   <span data-ttu-id="1fd78-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="1fd78-110">System.WorkflowServices.dll</span></span>  
  
-   <span data-ttu-id="1fd78-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="1fd78-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
-   <span data-ttu-id="1fd78-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="1fd78-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
-   <span data-ttu-id="1fd78-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="1fd78-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="1fd78-114">因此，使用已被取代之 WF 3 應用程式開發介面的客戶，將會遇到類似下列訊息的建置警告：</span><span class="sxs-lookup"><span data-stu-id="1fd78-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="1fd78-115">**警告 BC40000: X 已過時： WF 3 型別已被取代。請改用 WF 4。**</span><span class="sxs-lookup"><span data-stu-id="1fd78-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="1fd78-116">在未來的發行版本中，我們會將這些型別從 .NET Framework 移除，但我們尚未決定時間範圍 (不是在 4.5)。</span><span class="sxs-lookup"><span data-stu-id="1fd78-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="1fd78-117">目前這個步驟可讓我們向客戶傳達我們的方向，讓他們有大量的時間可以移至新的 WF4 模型。</span><span class="sxs-lookup"><span data-stu-id="1fd78-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="1fd78-118">我們將當然，繼續支援這些 WF 3 型別[Microsoft 支援週期原則](http://aka.ms/MicrosoftSupportLifecycle)。</span><span class="sxs-lookup"><span data-stu-id="1fd78-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](http://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="1fd78-119">現有的 WF3 應用程式將會在 .NET 4.5 上執行，而不會有問題，而且 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 會支援最新和現有的 WF3 方案。</span><span class="sxs-lookup"><span data-stu-id="1fd78-119">Existing WF3 applications will run without issue on .NET 4.5, and [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="1fd78-120"><xref:System.Workflow.Activities.Rules> 命名空間中與規則相關的型別在 WF 4.5 中並沒有替代項目，所以尚未被取代。</span><span class="sxs-lookup"><span data-stu-id="1fd78-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="1fd78-121">客戶想要移轉到 WF 4 其應用程式會尋找說明[工作流程 4 移轉指引](migration-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="1fd78-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
