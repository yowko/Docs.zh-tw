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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60e8d01ad32e10f06191f7e0b38dcb648780ba29
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="customizing-the-workflow-design-experience"></a>自訂工作流程設計經驗
在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 中，設計自訂活動及重新裝載 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] 的案例已大幅簡化。 無論開發或部署都變得更加容易、更有彈性。 關鍵的基礎結構變更是，新的活動設計工具程式設計模型是根據 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 建置的， 因此，您可以非常輕易地透過宣告的方式定義活動設計工具，以及將 [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] 重新裝載於其他應用程式中。 重新裝載時，可開發自訂運算式編輯器以支援 IntelliSense 或簡化的運算式網域。 使用工作流程服務，與 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 整合變得更加緊密。 自訂活動設計工具和模型項目樹狀可用來加強重新裝載工作流程設計工具中的設計階段經驗。  
  
## <a name="in-this-section"></a>本章節內容  
 [使用自訂活動設計工具與範本](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)  
 描述如何建立新的自訂活動設計工具和範本。  
  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 描述如何在 [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] 之外重新裝載 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，以及如何顯示驗證錯誤。  
  
 [使用自訂運算式編輯器](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)  
 描述如何實作自訂運算式編輯器，與重新裝載於 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 之外的工作流程設計工具搭配使用。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Activities.Presentation.ActivityDesigner>  
  
## <a name="see-also"></a>另請參閱  
 [擴充 Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/extend.md)  
 [設計工具](../../../docs/framework/windows-workflow-foundation/samples/designer.md)  
 [自訂活動設計工具](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)  
 [重新裝載設計工具](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)
