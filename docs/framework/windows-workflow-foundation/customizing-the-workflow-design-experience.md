---
title: 自訂工作流程設計經驗
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 926edb4478551affa03619f44ee886d5eb591e4d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637239"
---
# <a name="customizing-the-workflow-design-experience"></a>自訂工作流程設計經驗

在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中，設計自訂活動及重新裝載 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 的案例已大幅簡化。 無論開發或部署都變得更加容易、更有彈性。 索引鍵的基礎結構變更為新的活動設計工具程式設計模型建置在 Windows Presentation Foundation (WPF)。 因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。 重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。 與 Windows Communication Foundation (WCF) 的整合變得更順暢的工作流程服務使用。 自訂活動設計工具和模型項目樹狀結構可用來加強重新裝載工作流程設計工具中的設計階段經驗。

## <a name="in-this-section"></a>本節內容

 [使用自訂活動設計工具與範本](using-custom-activity-designers-and-templates.md)

 描述如何建立新的自訂活動設計工具和範本。

 [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)

 描述如何重新裝載[!INCLUDE[wfd1](../../../includes/wfd1-md.md)]之外，Visual Studio，以及如何顯示驗證錯誤。

 [使用自訂運算式編輯器](using-a-custom-expression-editor.md)

 描述如何實作自訂運算式編輯器，以搭配 Visual Studio 2010 之外重新裝載的工作流程設計工具。

## <a name="reference"></a>參考資料

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>另請參閱

- [擴充 Windows Workflow Foundation](extend.md)
- [設計工具](./samples/designer.md)
- [自訂活動設計工具](./samples/custom-activity-designers.md)
- [設計工具重新裝載](./samples/designer-rehosting.md)
