---
title: 控制 WCF 服務主機的自動啟動功能
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255074"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="d2abf-102">控制 WCF 服務主機的自動啟動功能</span><span class="sxs-lookup"><span data-stu-id="d2abf-102">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="d2abf-103">當您在包含多個專案的相同) 方案中，針對 WCF 服務程式庫專案的 Windows Communication Foundation (WCF) 服務主機 ( # A0 Visual Studio 時，您可以控制該專案的自動啟動功能。</span><span class="sxs-lookup"><span data-stu-id="d2abf-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="d2abf-104">若要這樣做，請在 **方案總管** 中的 WCF 服務專案上按一下滑鼠右鍵，選擇 [ **屬性**]，然後按一下 [ **WCF 選項** ] 索引標籤。預設會啟用 [在 **相同方案中偵錯工具時啟動 WCF 服務主機** ] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d2abf-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="d2abf-105">您可以清除此方塊，讓這個特定專案的 WCF 服務主機不會在相同方案中的另一個專案進行調試時啟動。</span><span class="sxs-lookup"><span data-stu-id="d2abf-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="d2abf-106">這個行為不會影響這個專案的 F5 偵錯或是 [加入服務參考] 等功能。</span><span class="sxs-lookup"><span data-stu-id="d2abf-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="d2abf-107">這個選項可供下列專案使用：</span><span class="sxs-lookup"><span data-stu-id="d2abf-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="d2abf-108">WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="d2abf-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="d2abf-109">循序工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="d2abf-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="d2abf-110">狀態機器工作流程服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="d2abf-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="d2abf-111">新聞訂閱服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="d2abf-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2abf-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2abf-112">See also</span></span>

- [<span data-ttu-id="d2abf-113">WCF 服務主機 (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="d2abf-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
