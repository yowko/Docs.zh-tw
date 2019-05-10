---
title: Windows Workflow Foundation 中被取代的類型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: c8325e60d708b53e1701a980355d5d2bf20e8a4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644960"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="3ac83-102">Windows Workflow Foundation 中被取代的類型</span><span class="sxs-lookup"><span data-stu-id="3ac83-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="3ac83-103">在 .NET 4 中，工作流程小組在 <xref:System.Activities> 命名空間中發行了全新的工作流程引擎。</span><span class="sxs-lookup"><span data-stu-id="3ac83-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="3ac83-104">.NET 4.5 Beta 版本中，我們要標記"WF 3"中類型的大部分<xref:System.Workflow.Activities>， <xref:System.Workflow.ComponentModel>，和<xref:System.Workflow.Runtime>為已過時的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3ac83-104">With the release of .NET 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>  
  
## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="3ac83-105">過時的命名空間和工具</span><span class="sxs-lookup"><span data-stu-id="3ac83-105">Obsolete namespaces and tools</span></span>  
 <span data-ttu-id="3ac83-106">下列組件含有一個或多個將會被取代的公用型別：</span><span class="sxs-lookup"><span data-stu-id="3ac83-106">The following assemblies have one or more public types that will be deprecated:</span></span>  
  
- <span data-ttu-id="3ac83-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="3ac83-107">System.Workflow.Activities.dll</span></span>  
  
- <span data-ttu-id="3ac83-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="3ac83-108">System.Workflow.ComponentModel.dll</span></span>  
  
- <span data-ttu-id="3ac83-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="3ac83-109">System.Workflow.Runtime.dll</span></span>  
  
- <span data-ttu-id="3ac83-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="3ac83-110">System.WorkflowServices.dll</span></span>  
  
- <span data-ttu-id="3ac83-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="3ac83-111">Microsoft.Workflow.DebugController.dll</span></span>  
  
- <span data-ttu-id="3ac83-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="3ac83-112">Microsoft.Workflow.Compiler.exe</span></span>  
  
- <span data-ttu-id="3ac83-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="3ac83-113">Wfc.exe</span></span>  
  
 <span data-ttu-id="3ac83-114">因此，使用已被取代之 WF 3 應用程式開發介面的客戶，將會遇到類似下列訊息的建置警告：</span><span class="sxs-lookup"><span data-stu-id="3ac83-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>  
  
 <span data-ttu-id="3ac83-115">**警告 BC40000:X 是已經過時：WF 3 型別已被取代。請改用 WF 4。**</span><span class="sxs-lookup"><span data-stu-id="3ac83-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="3ac83-116">在未來的發行版本中，我們會將這些型別從 .NET Framework 移除，但我們尚未決定時間範圍 (不是在 4.5)。</span><span class="sxs-lookup"><span data-stu-id="3ac83-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="3ac83-117">目前這個步驟可讓我們向客戶傳達我們的方向，讓他們有大量的時間可以移至新的 WF4 模型。</span><span class="sxs-lookup"><span data-stu-id="3ac83-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="3ac83-118">我們當然會繼續支援這些 WF 3 型別[Microsoft 支援週期原則](https://aka.ms/MicrosoftSupportLifecycle)。</span><span class="sxs-lookup"><span data-stu-id="3ac83-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](https://aka.ms/MicrosoftSupportLifecycle).</span></span> <span data-ttu-id="3ac83-119">現有的 WF3 應用程式時，會在.NET 4.5 上執行不會發生問題，且 Visual Studio 2012 支援新的和現有的 wf3 方案。</span><span class="sxs-lookup"><span data-stu-id="3ac83-119">Existing WF3 applications will run without issue on .NET 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>  
  
 <span data-ttu-id="3ac83-120"><xref:System.Workflow.Activities.Rules> 命名空間中與規則相關的型別在 WF 4.5 中並沒有替代項目，所以尚未被取代。</span><span class="sxs-lookup"><span data-stu-id="3ac83-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>  
  
 <span data-ttu-id="3ac83-121">想要移轉到 WF 4 應用程式的客戶會發現協助[工作流程 4 移轉指引](migration-guidance.md)。</span><span class="sxs-lookup"><span data-stu-id="3ac83-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
