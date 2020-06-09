---
title: 裝載工作流程服務概觀
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 10ea35fc1988e1b3e6ceb44aca098e63bfc7d7e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597289"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="81172-102">裝載工作流程服務概觀</span><span class="sxs-lookup"><span data-stu-id="81172-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="81172-103">您必須裝載工作流程服務，才能加以執行。</span><span class="sxs-lookup"><span data-stu-id="81172-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="81172-104"><xref:System.ServiceModel.WorkflowServiceHost> 是現成的工作流程主機，它支援多個執行個體、組態和 WCF 訊息 (不過，這些工作流程不需要使用訊息，就能夠裝載)。</span><span class="sxs-lookup"><span data-stu-id="81172-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="81172-105">此外，它也會透過一組服務行為，與持續性、追蹤和執行個體控制項整合。</span><span class="sxs-lookup"><span data-stu-id="81172-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="81172-106">就像 WCF 的 <xref:System.ServiceModel.ServiceHost> 一樣，<xref:System.ServiceModel.WorkflowServiceHost> 可以在任何 Managed .NET 應用程式中自我裝載，也可以在 IIS / WAS 中 Web 裝載 (成為 .xamlx 檔案)。</span><span class="sxs-lookup"><span data-stu-id="81172-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="81172-107">本節中的主題描述如何裝載工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="81172-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81172-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="81172-108">In This Section</span></span>  
 [<span data-ttu-id="81172-109">裝載工作流程服務</span><span class="sxs-lookup"><span data-stu-id="81172-109">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="81172-110">描述如何裝載工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="81172-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="81172-111">工作流程服務主機內部</span><span class="sxs-lookup"><span data-stu-id="81172-111">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="81172-112">描述 <xref:System.ServiceModel.WorkflowServiceHost> 如何處理傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="81172-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="81172-113">工作流程服務主機擴充性</span><span class="sxs-lookup"><span data-stu-id="81172-113">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="81172-114">描述如何擴充工作流程服務主機的功能。</span><span class="sxs-lookup"><span data-stu-id="81172-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="81172-115">工作流程控制端點</span><span class="sxs-lookup"><span data-stu-id="81172-115">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="81172-116">描述如何定義可讓您建立工作流程執行個體的端點。</span><span class="sxs-lookup"><span data-stu-id="81172-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="81172-117">如何：使用 Windows Server App Fabric 裝載工作流程服務</span><span class="sxs-lookup"><span data-stu-id="81172-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="81172-118">示範如何在 Windows Server App Fabric 中裝載現有的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="81172-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="81172-119">設定 WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="81172-119">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="81172-120">描述如何控制持續性、追蹤、閒置和未處理的例外狀況行為。</span><span class="sxs-lookup"><span data-stu-id="81172-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="81172-121">參考</span><span class="sxs-lookup"><span data-stu-id="81172-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="81172-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="81172-122">Related Sections</span></span>  
 [<span data-ttu-id="81172-123">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="81172-123">Workflow Services</span></span>](workflow-services.md)
