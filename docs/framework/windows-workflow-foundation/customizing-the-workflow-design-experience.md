---
title: 自訂工作流程設計經驗
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141921"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="6dba9-102">自訂工作流程設計經驗</span><span class="sxs-lookup"><span data-stu-id="6dba9-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="6dba9-103">在 .NET Framework 4 中，設計自訂活動和重新裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 的案例已大幅簡化。</span><span class="sxs-lookup"><span data-stu-id="6dba9-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="6dba9-104">無論開發或部署都變得更加容易、更有彈性。</span><span class="sxs-lookup"><span data-stu-id="6dba9-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="6dba9-105">關鍵的基礎結構變更是，新的活動設計工具程式設計模型是根據 Windows Presentation Foundation （WPF）所建立。</span><span class="sxs-lookup"><span data-stu-id="6dba9-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="6dba9-106">因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。</span><span class="sxs-lookup"><span data-stu-id="6dba9-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="6dba9-107">重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。</span><span class="sxs-lookup"><span data-stu-id="6dba9-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="6dba9-108">使用工作流程服務時，與 Windows Communication Foundation （WCF）的整合已變得更順暢。</span><span class="sxs-lookup"><span data-stu-id="6dba9-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="6dba9-109">自訂活動設計工具和模型項目樹狀結構可用來加強重新裝載工作流程設計工具中的設計階段經驗。</span><span class="sxs-lookup"><span data-stu-id="6dba9-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6dba9-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="6dba9-110">In This Section</span></span>

 [<span data-ttu-id="6dba9-111">使用自訂活動設計工具與範本</span><span class="sxs-lookup"><span data-stu-id="6dba9-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="6dba9-112">描述如何建立新的自訂活動設計工具和範本。</span><span class="sxs-lookup"><span data-stu-id="6dba9-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="6dba9-113">重新裝載工作流程設計工具</span><span class="sxs-lookup"><span data-stu-id="6dba9-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="6dba9-114">描述如何在 Visual Studio 外部重新裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]，以及如何顯示驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="6dba9-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="6dba9-115">使用自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="6dba9-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="6dba9-116">描述如何執行自訂表格達式編輯器，以搭配在 Visual Studio 2010 以外重新裝載的工作流程設計工具使用。</span><span class="sxs-lookup"><span data-stu-id="6dba9-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="6dba9-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="6dba9-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="6dba9-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="6dba9-118">See also</span></span>

- [<span data-ttu-id="6dba9-119">擴充 Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="6dba9-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="6dba9-120">設計工具</span><span class="sxs-lookup"><span data-stu-id="6dba9-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="6dba9-121">自訂活動設計工具</span><span class="sxs-lookup"><span data-stu-id="6dba9-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="6dba9-122">設計工具重新裝載</span><span class="sxs-lookup"><span data-stu-id="6dba9-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
