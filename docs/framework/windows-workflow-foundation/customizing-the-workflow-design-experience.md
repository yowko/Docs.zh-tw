---
title: "自訂工作流程設計經驗"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9916e30812e167e108a1ca9b958aa6d15fbd1f41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="ab863-102">自訂工作流程設計經驗</span><span class="sxs-lookup"><span data-stu-id="ab863-102">Customizing the Workflow Design Experience</span></span>
<span data-ttu-id="ab863-103">在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中，設計自訂活動及重新裝載 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 的案例已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="ab863-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="ab863-104">無論開發或部署都變得更加容易、更有彈性。</span><span class="sxs-lookup"><span data-stu-id="ab863-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="ab863-105">關鍵的基礎結構變更是，新的活動設計工具程式設計模型是根據 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 建置的，</span><span class="sxs-lookup"><span data-stu-id="ab863-105">The key infrastructural change is that the new activity designer programming model is built upon [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].</span></span> <span data-ttu-id="ab863-106">因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。</span><span class="sxs-lookup"><span data-stu-id="ab863-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="ab863-107">重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。</span><span class="sxs-lookup"><span data-stu-id="ab863-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="ab863-108">使用工作流程服務，與 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 整合變得更加緊密。</span><span class="sxs-lookup"><span data-stu-id="ab863-108">The integration with [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] has become more seamless with use of workflow services.</span></span> <span data-ttu-id="ab863-109">自訂活動設計工具和模型項目樹狀可用來加強重新裝載工作流程設計工具中的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="ab863-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab863-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ab863-110">In This Section</span></span>  
 [<span data-ttu-id="ab863-111">使用自訂活動設計工具與範本</span><span class="sxs-lookup"><span data-stu-id="ab863-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 <span data-ttu-id="ab863-112">描述如何建立新的自訂活動設計工具和範本。</span><span class="sxs-lookup"><span data-stu-id="ab863-112">Describes how to create new custom activity designers and templates.</span></span>  
  
 [<span data-ttu-id="ab863-113">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="ab863-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 <span data-ttu-id="ab863-114">描述如何在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 之外重新裝載 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，以及如何顯示驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab863-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] and how to display validation errors.</span></span>  
  
 [<span data-ttu-id="ab863-115">使用自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="ab863-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 <span data-ttu-id="ab863-116">描述如何實作自訂運算式編輯器，與重新裝載於 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 之外的工作流程設計工具搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ab863-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ab863-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="ab863-117">Reference</span></span>  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a><span data-ttu-id="ab863-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab863-118">See Also</span></span>  
 [<span data-ttu-id="ab863-119">擴充 Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="ab863-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [<span data-ttu-id="ab863-120">設計工具</span><span class="sxs-lookup"><span data-stu-id="ab863-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [<span data-ttu-id="ab863-121">自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="ab863-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [<span data-ttu-id="ab863-122">重新裝載設計工具</span><span class="sxs-lookup"><span data-stu-id="ab863-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
