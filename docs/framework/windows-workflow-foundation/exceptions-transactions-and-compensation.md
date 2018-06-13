---
title: 例外狀況、異動與補償
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: 346b07cd89c4071088676235d457930637b71549
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512206"
---
# <a name="exceptions-transactions-and-compensation"></a>例外狀況、異動與補償
[!INCLUDE[wf1](../../../includes/wf1-md.md)] 提供數種不同的機制，可用於處理工作流程中的執行階段錯誤狀況。 工作流程可以合併運用例外狀況處理常式、異動、取消與補償來處理錯誤狀況，並從錯誤狀況正常復原。  
  
## <a name="in-this-section"></a>本節內容  
 [例外狀況](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 示範如何使用 <xref:System.Activities.Statements.TryCatch> 活動處理工作流程中的例外狀況。  
  
 [異動](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 示範如何使用 <xref:System.Activities.Statements.TransactionScope> 活動運用工作流程中的交易。  
  
 [補償](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 描述工作流程中的補償，並且示範如何使用 <xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate> 和 <xref:System.Activities.Statements.Confirm> 等補償活動。  
  
 [取消](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 描述如何使用內建活動以及自訂活動，在工作流程中執行取消處理。  
  
 [偵錯工作流程](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 描述如何偵錯工作流程。
