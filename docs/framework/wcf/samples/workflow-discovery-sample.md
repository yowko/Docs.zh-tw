---
title: 工作流程探索範例
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 44d1fed74782051a926ced95c49f3e3cb14f2b9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263772"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="92e45-102">工作流程探索範例</span><span class="sxs-lookup"><span data-stu-id="92e45-102">Workflow Discovery Sample</span></span>

<span data-ttu-id="92e45-103">此範例示範如何讓工作流程服務可以探索，以及如何撰寫可搜尋特定服務的自訂程式碼活動。</span><span class="sxs-lookup"><span data-stu-id="92e45-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="92e45-104">示範</span><span class="sxs-lookup"><span data-stu-id="92e45-104">Demonstrates</span></span>  

 <span data-ttu-id="92e45-105">探索尋找活動與工作流程使用方式</span><span class="sxs-lookup"><span data-stu-id="92e45-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="92e45-106">討論</span><span class="sxs-lookup"><span data-stu-id="92e45-106">Discussion</span></span>  

 <span data-ttu-id="92e45-107">在此範例的第一個部分中，工作流程服務可以使用組態變成可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="92e45-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="92e45-108">組態也可以用來正確套用具有自訂中繼資料 (如範圍) 的服務。</span><span class="sxs-lookup"><span data-stu-id="92e45-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="92e45-109">在用戶端上，此範例會使用自訂程式碼活動，這個活動會使用探索來搜尋符合特定合約的服務。</span><span class="sxs-lookup"><span data-stu-id="92e45-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="92e45-110">程式碼活動會輸出一個稍後由傳送活動使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="92e45-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="92e45-111">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="92e45-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="92e45-112">此範例會使用 HTTP 端點，此端點必須有適當的 URL Acl 才能執行 (如需詳細資料，請參閱設定 [HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)) 。</span><span class="sxs-lookup"><span data-stu-id="92e45-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="92e45-113">以更高的命令提示字元執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="92e45-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="92e45-114">如果您的 shell 不了解變數格式，請以您的網域和使用者名稱取代下列引數。</span><span class="sxs-lookup"><span data-stu-id="92e45-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> <span data-ttu-id="92e45-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="92e45-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92e45-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="92e45-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="92e45-117">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="92e45-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92e45-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="92e45-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
