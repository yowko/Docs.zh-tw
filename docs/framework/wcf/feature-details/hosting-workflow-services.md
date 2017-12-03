---
title: "裝載工作流程服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1bf0b63d3de750b5ec2aea41dcb6bb700385663a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="hosting-workflow-services"></a>裝載工作流程服務
您必須裝載工作流程服務，才能讓它回應傳入的訊息。 工作流程服務使用了 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 訊息基礎結構，因此會以類似的方式裝載。 就像 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一樣，工作流程服務可以裝載在任何 Managed 應用程式中、裝載在 Internet Information Services (IIS) 底下，或是裝載在 Windows Process Activation Services (WAS) 底下。 此外，工作流程服務也可以裝載在 Windows Server App Fabric 底下。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server App Fabric，請參閱[Windows Server App Fabric 文件](http://go.microsoft.com/fwlink/?LinkId=193037)， [AppFabric 主控功能](http://go.microsoft.com/fwlink/?LinkId=196494)，和[AppFabric 主控概念](http://go.microsoft.com/fwlink/?LinkId=196495)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]主機的各種方式[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務，請參閱[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="hosting-in-a-managed-application"></a>在 Managed 應用程式中裝載  
 若要在 Managed 應用程式中裝載工作流程服務，請使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 類別。 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 建構函式可讓您指定單一工作流程服務執行個體、工作流程服務定義，或是一個活動使用工作流程訊息的多個活動。 呼叫 <<!--zz xref:System.ServiceModel.Activities.WorkflowServiceHost.Open%2A--> `System.ServiceModel.Activities.WorkflowServiceHost.Open`>，會導致開始接聽傳入訊息的服務。  
  
## <a name="hosting-under-iis-or-was"></a>在 IIS 或 WAS 底下裝載  
 在 IIS 或 WAS 底下裝載工作流程服務，需要建立虛擬目錄，並且在虛擬目錄中放入定義服務及其行為的檔案。 在 IIS 或 WAS 底下裝載工作流程服務時，有幾個可能的方法：  
  
-   將定義工作流程服務的 .xamlx 檔案置入 IIS/WAS 虛擬目錄，與指定服務行為、端點及其他組態項目的 Web.config 檔案放在一起。  
  
-   將定義工作流程服務的 .xamlx 檔案置入 IIS/WAS 虛擬目錄。 這個 .xamlx 檔案指定要公開的端點。 端點是在 `WorkflowService.Endpoints` 項目中指定的，如下列範例所示。  
  
    ```xml  
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
      <WorkflowService.Endpoints>  
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">  
          <Endpoint.Binding>  
            <BasicHttpBinding />  
          </Endpoint.Binding>  
        </Endpoint>  
      </WorkflowService.Endpoints>  
    <!-- ... -->  
    </WorkflowService>  
    ```  
  
    > [!NOTE]
    >  行為不能在 .xamlx 檔案中指定，所以如果需要指定行為設定，就必須使用 Web.config。  
  
-   將定義工作流程服務的 .xamlx 檔案置入 IIS/WAS 虛擬目錄。 此外，請將 .svc 檔案放進虛擬目錄。 這個 .svc 檔案可讓您指定一個自訂的 Web 服務裝載處理站、套用自訂行為，或是從自訂位置載入組態。  
  
-   將包含活動的組件置入 IIS/WAS 虛擬目錄，該活動會使用多個 WCF 訊息活動。  
  
 定義工作流程服務的.xamlx 檔案必須包含 <`Service`> 根項目或根項目，其中包含衍生自任何型別<xref:System.Workflow.ComponentModel.Activity>。 使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 活動範本時，就會建立 .xamlx 檔案。 使用 WCF 工作流程服務範本時，就會建立 .xamlx 檔案。  
  
## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>在 Windows Server App Fabric 底下裝載工作流程服務  
 在 Windows Server App Fabric 底下裝載工作流程服務的方式與在 IIS/WAS 底下裝載的方式相同。 唯一的差異在於已安裝 Windows Server App Fabric 的事實。 Windows Server App Fabric 提供了一些加入至 Internet Information Services 管理員的工具，以及 Powershell 指令程式。 這些工具會簡化部署、管理和追蹤工作流程與 WCF 服務的作業。 。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Windows Server App Fabric，請參閱[Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=193037)  
  
## <a name="referencing-custom-activities"></a>參考自訂活動  
 參考自訂活動必須加入至 <`Assemblies`> 下一節 <`System.Web.Compilation`>，而它們會對應用程式定義域載入 XAML 還原序列化程式找不到型別。 這些設定可以在應用程式層級進行，如果設定值應該套用到電腦上的所有應用程式，則可以在根 Web.config 進行這些設定。  
  
## <a name="deployment"></a>部署  
 Web 部署工具的建立，是要讓部署的工作更容易進行。 此工具可讓您在 IIS 6.0 與 IIS 7.0 之間移轉應用程式、同步處理伺服器陣列，以及封裝、封存及部署 Web 應用程式。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][MS 部署工具](http://go.microsoft.com/fwlink/?LinkId=178690)  
  
## <a name="see-also"></a>另請參閱  
 [工作流程服務主機內部](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 [設定 WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)
