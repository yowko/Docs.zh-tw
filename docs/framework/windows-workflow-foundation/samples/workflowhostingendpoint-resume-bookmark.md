---
title: WorkflowHostingEndpoint 繼續書籤
ms.date: 03/30/2017
ms.assetid: a708064f-50b0-4751-b44e-d5410d08d451
ms.openlocfilehash: 5c3c996a73d8f88e925d459fae3eb785996eada4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340538"
---
# <a name="workflowhostingendpoint-resume-bookmark"></a>WorkflowHostingEndpoint 繼續書籤
這個範例示範 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 如何與 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 搭配使用以建立工作流程執行個體。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>、 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
## <a name="discussion"></a>討論  
 這個範例使用 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 來建立以 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載的工作流程執行個體。 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> 是 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的擴充點，可用於以下情形：  
  
-   建立新的工作流程執行個體。  
  
-   在裝載於 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的工作流程執行個體中繼續使用書籤。  
  
 包含的範例端點會公開合約，以提供作業來建立工作流程，以及傳回執行個體識別碼或建立具有特定識別碼的執行個體。 範例主控台應用程式會建立具有基本工作流程定義的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 執行個體，並將 `CreationEndpoint` 加入至主機。 接著會在端點上呼叫 `Create` 作業，以建立新的工作流程執行個體。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 建置方案。  
  
2. 執行應用程式。 建立工作流程執行個體之後，`CreationEndpoint` 主控台會顯示包含執行個體識別碼的訊息。 訊息"Hello World ！" 列印書籤成功繼續時工作流程。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ResumeBookmarkEndpoint`
