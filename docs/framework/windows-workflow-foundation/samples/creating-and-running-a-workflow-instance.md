---
title: 建立與執行工作流程執行個體
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016053"
---
# <a name="creating-and-running-a-workflow-instance"></a>建立與執行工作流程執行個體

這個範例示範如何執行工作流程執行個體。 範例中會示範如何以同步和非同步方式執行。

## <a name="demonstrates"></a>示範

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>討論

範例的第一個部分會使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A>。 這是執行工作流程的最基本方式。 使用 <xref:System.Activities.WorkflowInvoker.Invoke%2A> 執行的工作流程會以同步方式執行。

範例的第二部分使用 <xref:System.Activities.WorkflowApplication> 類別。 <xref:System.Activities.WorkflowApplication> 可讓您更充分掌控每一個執行個體，包括與執行中工作流程進行互動以及透過非同步方式執行工作流程的能力。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>另請參閱

- [使用 WorkflowInvoker 與 WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
