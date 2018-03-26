---
title: 重新命名 WCF 服務
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14235a65-b1c5-409d-b6cc-a979acd54bbd
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2ab3d780f85131fc7adf24c5f420bd5fe643d9e
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="renaming-a-wcf-service"></a><span data-ttu-id="fc612-102">重新命名 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="fc612-102">Renaming a WCF Service</span></span>
<span data-ttu-id="fc612-103">本主題說明如何重新命名 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="fc612-103">This topic describes how you can rename a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service.</span></span>  
  
## <a name="renaming-a-wcf-service"></a><span data-ttu-id="fc612-104">重新命名 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="fc612-104">Renaming a WCF Service</span></span>  
 <span data-ttu-id="fc612-105">請執行下列步驟，以重新命名 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 範本中的服務。</span><span class="sxs-lookup"><span data-stu-id="fc612-105">Perform the following steps to rename a service in a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] template,</span></span>  
  
-   <span data-ttu-id="fc612-106">變更實作服務的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="fc612-106">Change the name of the class that implements the service.</span></span>  
  
-   <span data-ttu-id="fc612-107">在服務的組態檔中，如下列範例所示，將服務的名稱變更為您選擇的新名稱。</span><span class="sxs-lookup"><span data-stu-id="fc612-107">In the configuration file of the service, change the name of the service to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="fc612-108">視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc612-108">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service name="WcfService.NewName">  
      </service>  
   </services>  
</system.servicemodel>  
```  
  
-   <span data-ttu-id="fc612-109">如果您的服務是 Webhosted，則服務會使用 \*.svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc612-109">If your service is webhosted, it uses an \*.svc file.</span></span> <span data-ttu-id="fc612-110">如下列範例所示，開啟 svc 檔案並修改您的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="fc612-110">Open the svc file and modify the name of your service as indicated in the following example.</span></span> <span data-ttu-id="fc612-111">對於自我裝載應用程式，則不需要執行這個步驟，因為沒有 svc 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc612-111">This step is not necessary for self-hosted applications, as there is no svc file.</span></span>  
  
```  
<%@ ServiceHost Service="WcfService.NewName">  
```  
  
## <a name="renaming-a-wcf-service-contract"></a><span data-ttu-id="fc612-112">重新命名 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="fc612-112">Renaming a WCF Service Contract</span></span>  
  
-   <span data-ttu-id="fc612-113">請執行下列步驟，以重新命名服務合約。</span><span class="sxs-lookup"><span data-stu-id="fc612-113">Perform the following steps to rename the service contract,</span></span>  
  
-   <span data-ttu-id="fc612-114">變更服務合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="fc612-114">Change the name of the service contract.</span></span>  
  
-   <span data-ttu-id="fc612-115">在服務的組態檔中，如下列範例所示，將服務合約的名稱變更為您選擇的新名稱。</span><span class="sxs-lookup"><span data-stu-id="fc612-115">In the configuration file of the service, change the name of the service contract to the new name you have chosen, as indicated in the following example.</span></span> <span data-ttu-id="fc612-116">視您的裝載模型而定，組態檔可能是 app.config 或 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="fc612-116">The configuration file can be either app.config or web.config file depending on your hosting model.</span></span>  
  
```xml  
<system.servicemodel>  
   <services>  
      <service>  
         <endpoint contract="WcfService.NewContractName" />  
      </service>  
   </services>  
</system.servicemodel>  
```
