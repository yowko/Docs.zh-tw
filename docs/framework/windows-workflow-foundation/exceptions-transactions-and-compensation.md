---
title: "例外狀況、交易與補償"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be803580a4d8ed195222e5960cfa6e26804d91c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="140c7-102">例外狀況、異動與補償</span><span class="sxs-lookup"><span data-stu-id="140c7-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="140c7-103"> 提供數種不同的機制，可用於處理工作流程中的執行階段錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="140c7-103"> provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="140c7-104">工作流程可以合併運用例外狀況處理常式、異動、取消與補償來處理錯誤狀況，並從錯誤狀況正常復原。</span><span class="sxs-lookup"><span data-stu-id="140c7-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="140c7-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="140c7-105">In This Section</span></span>  
 [<span data-ttu-id="140c7-106">例外狀況</span><span class="sxs-lookup"><span data-stu-id="140c7-106">Exceptions</span></span>](../../../docs/framework/windows-workflow-foundation/exceptions.md)  
 <span data-ttu-id="140c7-107">示範如何使用 <xref:System.Activities.Statements.TryCatch> 活動處理工作流程中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="140c7-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="140c7-108">異動</span><span class="sxs-lookup"><span data-stu-id="140c7-108">Transactions</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md)  
 <span data-ttu-id="140c7-109">示範如何使用 <xref:System.Activities.Statements.TransactionScope> 活動運用工作流程中的交易。</span><span class="sxs-lookup"><span data-stu-id="140c7-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="140c7-110">補償</span><span class="sxs-lookup"><span data-stu-id="140c7-110">Compensation</span></span>](../../../docs/framework/windows-workflow-foundation/compensation.md)  
 <span data-ttu-id="140c7-111">描述工作流程中的補償，並且示範如何使用 <xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate> 和 <xref:System.Activities.Statements.Confirm> 等補償活動。</span><span class="sxs-lookup"><span data-stu-id="140c7-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="140c7-112">取消</span><span class="sxs-lookup"><span data-stu-id="140c7-112">Cancellation</span></span>](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="140c7-113">描述如何使用內建活動以及自訂活動，在工作流程中執行取消處理。</span><span class="sxs-lookup"><span data-stu-id="140c7-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="140c7-114">偵錯工作流程</span><span class="sxs-lookup"><span data-stu-id="140c7-114">Debugging Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/debugging-workflows.md)  
 <span data-ttu-id="140c7-115">描述如何偵錯工作流程。</span><span class="sxs-lookup"><span data-stu-id="140c7-115">Describes how to debug workflows.</span></span>
