---
title: 例外狀況、異動與補償
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774006"
---
# <a name="exceptions-transactions-and-compensation"></a>例外狀況、異動與補償
[!INCLUDE[wf1](../../../includes/wf1-md.md)] 提供數種不同的機制，可用於處理工作流程中的執行階段錯誤狀況。 工作流程可以合併運用例外狀況處理常式、交易、取消與補償來處理錯誤狀況，並從錯誤狀況正常復原。  
  
## <a name="in-this-section"></a>本節內容  
 [例外狀況](exceptions.md)  
 示範如何使用 <xref:System.Activities.Statements.TryCatch> 活動處理工作流程中的例外狀況。  
  
 [異動](workflow-transactions.md)  
 示範如何使用 <xref:System.Activities.Statements.TransactionScope> 活動運用工作流程中的交易。  
  
 [補償](compensation.md)  
 描述工作流程中的補償，並且示範如何使用 <xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate> 和 <xref:System.Activities.Statements.Confirm> 等補償活動。  
  
 [取消](modeling-cancellation-behavior-in-workflows.md)  
 描述如何使用內建活動以及自訂活動，在工作流程中執行取消處理。  
  
 [偵錯工作流程](debugging-workflows.md)  
 描述如何偵錯工作流程。
