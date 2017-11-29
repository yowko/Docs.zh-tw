---
title: "Windows Workflow Foundation 組態結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ae70357-b150-4342-8f2a-d5eb6f9c6a0d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e83b85d970f36745bb1a0bcf04253c678764805e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="windows-workflow-foundation-configuration-schema"></a><span data-ttu-id="08f2f-102">Windows Workflow Foundation 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="08f2f-102">Windows Workflow Foundation Configuration Schema</span></span>
[!INCLUDE[wf](../../../../../includes/wf-md.md)]<span data-ttu-id="08f2f-103"> 組態項目可讓您設定工作流程應用程式。</span><span class="sxs-lookup"><span data-stu-id="08f2f-103"> configuration elements enable you to configure workflow applications.</span></span> <span data-ttu-id="08f2f-104">針對工作流程應用程式，您可以設定追蹤 (Tracking) 與追蹤 (Tracing) 之外的其他功能。</span><span class="sxs-lookup"><span data-stu-id="08f2f-104">For a workflow application, you can configure among other things, tracking and tracing.</span></span> <span data-ttu-id="08f2f-105">如需追蹤 (tracking) 與追蹤 (tracing) 的詳細資訊，請參閱[工作流程追蹤及追蹤](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="08f2f-105">For more information about tracking and tracing, see [Workflow Tracking and Tracing](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="08f2f-106">針對工作流程服務，您也可以使用 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 組態項目。</span><span class="sxs-lookup"><span data-stu-id="08f2f-106">For workflow services, you can also use [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] configuration elements.</span></span> <span data-ttu-id="08f2f-107">如需 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 的詳細資料，請參閱 [WCF 組態結構描述](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md)。</span><span class="sxs-lookup"><span data-stu-id="08f2f-107">For more details about [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], see [WCF Configuration Schema](../../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="08f2f-108">由於組態檔採用 XML 格式，因此，如果要使用文字編輯器手動編輯這些檔案，則必須熟悉 XML。</span><span class="sxs-lookup"><span data-stu-id="08f2f-108">Because configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="08f2f-109">否則，您可能會碰到 XML 項目標記或屬性找不到等問題，</span><span class="sxs-lookup"><span data-stu-id="08f2f-109">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="08f2f-110">因為 XML 項目標記與屬性有區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="08f2f-110">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08f2f-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="08f2f-111">In This Section</span></span>  
 [<span data-ttu-id="08f2f-112">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="08f2f-112">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/system-servicemodel-of-workflow.md)  
 <span data-ttu-id="08f2f-113">描述 **ServiceModel** 項目。</span><span class="sxs-lookup"><span data-stu-id="08f2f-113">Describes the **ServiceModel** element.</span></span>
