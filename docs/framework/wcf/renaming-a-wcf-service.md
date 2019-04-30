---
title: 重新命名 WCF 服務
ms.date: 03/30/2017
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
ms.openlocfilehash: a215523b92757e3bde1dae2e50de22169020e870
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955138"
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="43ef1-102">重新命名 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="43ef1-102">Renaming a WCF Service</span></span>
<span data-ttu-id="43ef1-103">本主題描述如何重新命名 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="43ef1-103">This topic describes how you can rename a Windows Communication Foundation (WCF) service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="43ef1-104">重新命名 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="43ef1-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="43ef1-105">執行下列步驟來重新命名服務，以在 Windows Communication Foundation (WCF) 範本中，</span><span class="sxs-lookup"><span data-stu-id="43ef1-105">Perform the following steps to rename a service in a Windows Communication Foundation (WCF) template,</span></span>  
  
- <span data-ttu-id="43ef1-106">變更實作服務的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="43ef1-106">Change the name of the class that implements the service.</span></span>  
  
- <span data-ttu-id="43ef1-107">在服務的組態檔中，如下列範例所示，將服務的名稱變更為您選擇的新名稱。</span><span class="sxs-lookup"><span data-stu-id="43ef1-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="43ef1-108">視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="43ef1-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
- <span data-ttu-id="43ef1-109">如果您的服務是 Webhosted，則服務會使用 \*.svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="43ef1-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="43ef1-110">如下列範例所示，開啟 svc 檔案並修改您的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="43ef1-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="43ef1-111">對於自我裝載應用程式，則不需要執行這個步驟，因為沒有 svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="43ef1-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="43ef1-112">重新命名 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="43ef1-112">Renaming a WCF Service Contract</span></span>  
  
- <span data-ttu-id="43ef1-113">請執行下列步驟，以重新命名服務合約。</span><span class="sxs-lookup"><span data-stu-id="43ef1-113">Perform the following steps to rename the service contract,</span></span>  
  
- <span data-ttu-id="43ef1-114">變更服務合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="43ef1-114">Change the name of the service contract.</span></span>  
  
- <span data-ttu-id="43ef1-115">在服務的組態檔中，如下列範例所示，將服務合約的名稱變更為您選擇的新名稱。</span><span class="sxs-lookup"><span data-stu-id="43ef1-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="43ef1-116">視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="43ef1-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
