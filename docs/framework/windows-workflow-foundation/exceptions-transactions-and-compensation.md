---
title: 例外狀況、異動與補償
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], error handling
ms.assetid: 694db4f9-7387-4b13-8f9f-b923b18c7490
ms.openlocfilehash: c4d66e252561ad7b896ff8092e80013c51bd463c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709467"
---
# <a name="exceptions-transactions-and-compensation"></a><span data-ttu-id="c52a3-102">例外狀況、異動與補償</span><span class="sxs-lookup"><span data-stu-id="c52a3-102">Exceptions, Transactions, and Compensation</span></span>
[!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="c52a3-103">提供數種不同的機制，可用於處理工作流程中的執行階段錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="c52a3-103">provides several different mechanisms for handling run-time error conditions in workflows.</span></span> <span data-ttu-id="c52a3-104">工作流程可以合併運用例外狀況處理常式、交易、取消與補償來處理錯誤狀況，並從錯誤狀況正常復原。</span><span class="sxs-lookup"><span data-stu-id="c52a3-104">Workflows can use a combination of exception handlers, transactions, cancellation, and compensation to handle and recover gracefully from error conditions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c52a3-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="c52a3-105">In This Section</span></span>  
 [<span data-ttu-id="c52a3-106">例外狀況</span><span class="sxs-lookup"><span data-stu-id="c52a3-106">Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="c52a3-107">示範如何使用 <xref:System.Activities.Statements.TryCatch> 活動處理工作流程中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c52a3-107">Demonstrates how to use the <xref:System.Activities.Statements.TryCatch> activity to handle exceptions in a workflow.</span></span>  
  
 [<span data-ttu-id="c52a3-108">異動</span><span class="sxs-lookup"><span data-stu-id="c52a3-108">Transactions</span></span>](workflow-transactions.md)  
 <span data-ttu-id="c52a3-109">示範如何使用 <xref:System.Activities.Statements.TransactionScope> 活動運用工作流程中的交易。</span><span class="sxs-lookup"><span data-stu-id="c52a3-109">Demonstrates how to use the <xref:System.Activities.Statements.TransactionScope> activity to use transactions in a workflow.</span></span>  
  
 [<span data-ttu-id="c52a3-110">補償</span><span class="sxs-lookup"><span data-stu-id="c52a3-110">Compensation</span></span>](compensation.md)  
 <span data-ttu-id="c52a3-111">描述工作流程中的補償，並且示範如何使用 <xref:System.Activities.Statements.CompensableActivity>、<xref:System.Activities.Statements.Compensate> 和 <xref:System.Activities.Statements.Confirm> 等補償活動。</span><span class="sxs-lookup"><span data-stu-id="c52a3-111">Describes compensation in workflows and demonstrates how to use compensation activities such as <xref:System.Activities.Statements.CompensableActivity>, <xref:System.Activities.Statements.Compensate>, and <xref:System.Activities.Statements.Confirm>.</span></span>  
  
 [<span data-ttu-id="c52a3-112">取消</span><span class="sxs-lookup"><span data-stu-id="c52a3-112">Cancellation</span></span>](modeling-cancellation-behavior-in-workflows.md)  
 <span data-ttu-id="c52a3-113">描述如何使用內建活動以及自訂活動，在工作流程中執行取消處理。</span><span class="sxs-lookup"><span data-stu-id="c52a3-113">Describes how to perform cancellation handling in workflows using built-in activities as well as custom activities.</span></span>  
  
 [<span data-ttu-id="c52a3-114">偵錯工作流程</span><span class="sxs-lookup"><span data-stu-id="c52a3-114">Debugging Workflows</span></span>](debugging-workflows.md)  
 <span data-ttu-id="c52a3-115">描述如何偵錯工作流程。</span><span class="sxs-lookup"><span data-stu-id="c52a3-115">Describes how to debug workflows.</span></span>
