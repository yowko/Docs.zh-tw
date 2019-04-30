---
title: 自訂工作流程設計經驗
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 2d6ef24d00baa4df6dfc8e0af69c1d489b79a41f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945986"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="40ebc-102">自訂工作流程設計經驗</span><span class="sxs-lookup"><span data-stu-id="40ebc-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="40ebc-103">在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中，設計自訂活動及重新裝載 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 的案例已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="40ebc-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="40ebc-104">無論開發或部署都變得更加容易、更有彈性。</span><span class="sxs-lookup"><span data-stu-id="40ebc-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="40ebc-105">索引鍵的基礎結構變更為新的活動設計工具程式設計模型建置在 Windows Presentation Foundation (WPF)。</span><span class="sxs-lookup"><span data-stu-id="40ebc-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="40ebc-106">因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。</span><span class="sxs-lookup"><span data-stu-id="40ebc-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="40ebc-107">重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。</span><span class="sxs-lookup"><span data-stu-id="40ebc-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="40ebc-108">與 Windows Communication Foundation (WCF) 的整合變得更順暢的工作流程服務使用。</span><span class="sxs-lookup"><span data-stu-id="40ebc-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="40ebc-109">自訂活動設計工具和模型項目樹狀結構可用來加強重新裝載工作流程設計工具中的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="40ebc-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="40ebc-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="40ebc-110">In This Section</span></span>

 [<span data-ttu-id="40ebc-111">使用自訂活動設計工具與範本</span><span class="sxs-lookup"><span data-stu-id="40ebc-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="40ebc-112">描述如何建立新的自訂活動設計工具和範本。</span><span class="sxs-lookup"><span data-stu-id="40ebc-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="40ebc-113">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="40ebc-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="40ebc-114">描述如何重新裝載[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]之外，Visual Studio，以及如何顯示驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="40ebc-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="40ebc-115">使用自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="40ebc-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="40ebc-116">描述如何實作自訂運算式編輯器，以搭配 Visual Studio 2010 之外重新裝載的工作流程設計工具。</span><span class="sxs-lookup"><span data-stu-id="40ebc-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="40ebc-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="40ebc-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="40ebc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40ebc-118">See also</span></span>

- [<span data-ttu-id="40ebc-119">擴充 Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="40ebc-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="40ebc-120">設計工具</span><span class="sxs-lookup"><span data-stu-id="40ebc-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="40ebc-121">自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="40ebc-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="40ebc-122">設計工具重新裝載</span><span class="sxs-lookup"><span data-stu-id="40ebc-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)