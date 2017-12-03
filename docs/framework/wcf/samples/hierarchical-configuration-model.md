---
title: "階層式組態模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcef9ebe1b4876e429da97b3e217dd32286e4d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="hierarchical-configuration-model"></a>階層式組態模型
此範例示範如何針對服務實作組態檔的階層。 它也會示範如何從階層中較高的層級繼承繫結、服務行為與端點行為。  
  
## <a name="sample-details"></a>範例詳細資料  
 針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 開發之其中一個功能是階層組態模型中的改進功能。 階層組態模型的範例是由 Machine.config -> Rootweb.config -> Web.config 所定義的範例。在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 中，於組態階層之較上層中定義的那些繫結與行為都會在沒有明確組態的情況下，加入至您的服務。 此範例示範如何能夠透過依賴在電腦或應用程式層級定義的組態項目，簡化您的服務組態。  
  
 這個範例由三個階層層級中定義的九個服務所組成。 `Service1` 位於根目錄。 `Service2` 和 `Service3` 從 `Service1` 繼承預設元素。 `Service4`、`Service5`、`Service6` 和 `Service7` 是在階層的第三個層級定義的，且從 `Service3` 繼承預設項目。 最後，`Service10` 和 `Service11` 則位於階層的第四個層級。  
  
 所有服務都會實作 `IDesc` 合約。 以下是 `IDesc` 介面的定義，這個定義會顯示在此介面中公開的方法。 `IDesc` 介面是在 Service1.cs 中定義的。  
  
```  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 由服務針對這些方法進行的實作相當直接。 `ListEndpoints` 會逐一查看所有服務端點，並傳回服務所擁有之所有端點的清單。 `ListServiceBehaviors` 會逐一查看加入至服務的所有行為，並傳回與服務相關聯之所有服務行為的清單。 `ListEndpointBehaviors` 以類似於 `ListServiceBehaviors` 的方式運作，但它會傳回端點行為的清單。  
  
 這個實作可讓用戶端了解服務公開多少端點，以及哪些服務行為和端點行為已加入至服務。 已經當做範例一部分實作的用戶端會將服務參考加入至方案中的所有服務，並針對每個服務顯示這些項目。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
#### <a name="to-run-the-client"></a>若要執行用戶端  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 ConfigHierarchicalModel.sln 檔案。  
  
2.  如果用戶端專案還未設定為啟始專案，請遵循下列步驟進行。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下方案，然後選取**屬性**。  
  
    2.  在**通用屬性**，選取**啟始專案**，然後按一下 **單一啟始專案**。  
  
    3.  從**單一啟始專案**下拉式清單中，選取**用戶端**。  
  
    4.  按一下**確定**以關閉對話方塊。  
  
3.  若要建置範例，請按下 CTRL+SHIFT+B。  
  
4.  若要執行用戶端，請按下 Ctrl+F5。  
  
> [!NOTE]
>  如果這些步驟沒有作用，則請使用下列步驟確認您的環境已正確設定。  
>   
>  1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
> 2.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
> 3.  若要執行範例單一或多個電腦組態，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 管理範例](http://go.microsoft.com/fwlink/?LinkId=193960)
