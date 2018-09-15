---
title: 工作流程探索範例
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45649558"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="742cb-102">工作流程探索範例</span><span class="sxs-lookup"><span data-stu-id="742cb-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="742cb-103">此範例示範如何讓工作流程服務可以探索，以及如何撰寫可搜尋特定服務的自訂程式碼活動。</span><span class="sxs-lookup"><span data-stu-id="742cb-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="742cb-104">示範</span><span class="sxs-lookup"><span data-stu-id="742cb-104">Demonstrates</span></span>  
 <span data-ttu-id="742cb-105">探索尋找活動與工作流程使用方式</span><span class="sxs-lookup"><span data-stu-id="742cb-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="742cb-106">討論</span><span class="sxs-lookup"><span data-stu-id="742cb-106">Discussion</span></span>  
 <span data-ttu-id="742cb-107">在此範例的第一個部分中，工作流程服務可以使用組態變成可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="742cb-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="742cb-108">組態也可以用來正確套用具有自訂中繼資料 (如範圍) 的服務。</span><span class="sxs-lookup"><span data-stu-id="742cb-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="742cb-109">在用戶端上，此範例會使用自訂程式碼活動，這個活動會使用探索來搜尋符合特定合約的服務。</span><span class="sxs-lookup"><span data-stu-id="742cb-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="742cb-110">程式碼活動會輸出一個稍後由傳送活動使用的 URI。</span><span class="sxs-lookup"><span data-stu-id="742cb-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="742cb-111">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="742cb-111">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="742cb-112">這個範例會使用 HTTP 端點，必須執行正確的 URL Acl (請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="742cb-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details).</span></span> <span data-ttu-id="742cb-113">以更高的命令提示字元執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="742cb-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="742cb-114">如果您的 Shell 不了解變數格式，請將 Domain 和 Username 替換成下列引數。</span><span class="sxs-lookup"><span data-stu-id="742cb-114">Substitute your Domain and Username for the following arguments if your shell does not understand the variable format.</span></span>  
  
     <span data-ttu-id="742cb-115">**netsh http add urlacl =http://+:8000/使用者 = %網域 %\\%username%**</span><span class="sxs-lookup"><span data-stu-id="742cb-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="742cb-116">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="742cb-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="742cb-117">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="742cb-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="742cb-118">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="742cb-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="742cb-119">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="742cb-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
