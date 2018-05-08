---
title: 重新命名 WCF 服務
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="renaming-a-wcf-service"></a>重新命名 WCF 服務
本主題描述如何重新命名 Windows Communication Foundation (WCF) 服務。  
  
## <a name="renaming-a-wcf-service"></a>重新命名 WCF 服務  
 執行下列步驟來重新命名 Windows Communication Foundation (WCF) 範本中的服務  
  
-   變更實作服務的類別名稱。  
  
-   在服務的組態檔中，如下列範例所示，將服務的名稱變更為您選擇的新名稱。 視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   如果您的服務是 Webhosted，則服務會使用 *.svc 檔案。 如下列範例所示，開啟 svc 檔案並修改您的服務名稱。 對於自我裝載應用程式，則不需要執行這個步驟，因為沒有 svc 檔案。  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a>重新命名 WCF 服務合約  
  
-   請執行下列步驟，以重新命名服務合約。  
  
-   變更服務合約的名稱。  
  
-   在服務的組態檔中，如下列範例所示，將服務合約的名稱變更為您選擇的新名稱。 視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
