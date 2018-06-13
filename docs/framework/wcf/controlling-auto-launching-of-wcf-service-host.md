---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809884"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="81099-102">控制 WCF 服務主機的自動啟動功能</span><span class="sxs-lookup"><span data-stu-id="81099-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="81099-103">當您偵錯包含多個專案的相同 Visual Studio 方案中另一個專案時，您可以控制 WCF 服務程式庫專案中，Windows Communication Foundation (WCF) 服務主機 (WcfSvcHost.exe) 的自動啟動功能。</span><span class="sxs-lookup"><span data-stu-id="81099-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="81099-104">若要這樣做，請以滑鼠右鍵按一下 WCF 服務專案中**方案總管 中**，選擇**屬性**，然後按一下**WCF 選項** 索引標籤。**啟動 WCF 服務主機相同方案中的另一個專案進行偵錯時**核取方塊預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="81099-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="81099-105">您可以清除方塊，以便在相同方案中的另一個專案進行偵錯時，將無法啟動這個特定專案的 WCF 服務主機。</span><span class="sxs-lookup"><span data-stu-id="81099-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="81099-106">這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。</span><span class="sxs-lookup"><span data-stu-id="81099-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="81099-107">這個選項可供下列專案使用：</span><span class="sxs-lookup"><span data-stu-id="81099-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="81099-108">WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="81099-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="81099-109">循序工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="81099-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="81099-110">狀態機器工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="81099-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="81099-111">新聞訂閱服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="81099-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81099-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81099-112">See Also</span></span>  
 [<span data-ttu-id="81099-113">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="81099-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
