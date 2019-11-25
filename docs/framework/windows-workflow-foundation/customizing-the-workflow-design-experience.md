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
# <a name="customizing-the-workflow-design-experience"></a>自訂工作流程設計經驗

在 .NET Framework 4 中，設計自訂活動和重新裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 的案例已大幅簡化。 無論開發或部署都變得更加容易、更有彈性。 關鍵的基礎結構變更是，新的活動設計工具程式設計模型是根據 Windows Presentation Foundation （WPF）所建立。 因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。 重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。 使用工作流程服務時，與 Windows Communication Foundation （WCF）的整合已變得更順暢。 自訂活動設計工具和模型項目樹狀結構可用來加強重新裝載工作流程設計工具中的設計階段經驗。

## <a name="in-this-section"></a>本章節內容

 [使用自訂活動設計工具與範本](using-custom-activity-designers-and-templates.md)

 描述如何建立新的自訂活動設計工具和範本。

 [重新裝載工作流程設計工具](rehosting-the-workflow-designer.md)

 描述如何在 Visual Studio 外部重新裝載 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]，以及如何顯示驗證錯誤。

 [使用自訂運算式編輯器](using-a-custom-expression-editor.md)

 描述如何執行自訂表格達式編輯器，以搭配在 Visual Studio 2010 以外重新裝載的工作流程設計工具使用。

## <a name="reference"></a>參考資料

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a>請參閱

- [擴充 Windows Workflow Foundation](extend.md)
- [設計工具](./samples/designer.md)
- [自訂活動設計工具](./samples/custom-activity-designers.md)
- [設計工具重新裝載](./samples/designer-rehosting.md)
