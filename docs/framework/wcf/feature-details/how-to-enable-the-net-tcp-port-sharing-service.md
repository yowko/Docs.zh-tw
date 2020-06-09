---
title: HOW TO：啟用 Net.TCP 連接埠共用服務
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 8b305b98d620636328866bce848411f395053485
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593124"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="23a49-102">HOW TO：啟用 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="23a49-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="23a49-103">Windows Communication Foundation （WCF）使用稱為 Net.tcp 埠共用服務的 Windows 服務，以加速跨多個進程共用 TCP 埠。</span><span class="sxs-lookup"><span data-stu-id="23a49-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="23a49-104">這項服務會安裝為 WCF 的一部分，但預設不會啟用服務做為安全性預防措施，因此必須在第一次使用之前手動啟用。</span><span class="sxs-lookup"><span data-stu-id="23a49-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="23a49-105">本主題說明如何使用 Microsoft Management Console (MMC) 嵌入式管理單元，來設定 Net TCP Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="23a49-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="23a49-106">啟用 Net.tcp 埠共用服務並手動啟動之後，請參閱[如何：將 WCF 服務設定為使用埠共用](how-to-configure-a-wcf-service-to-use-port-sharing.md)，以取得如何設定服務以使用此服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="23a49-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="23a49-107">如需使用 net.tcp：//埠共用的範例，請參閱[Net.tcp 埠共用範例](../samples/net-tcp-port-sharing-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="23a49-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="23a49-108">若要使用 MMC 來啟用 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="23a49-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="23a49-109">在 [開始] 功能表中，開啟 [命令提示字元] 視窗並輸入或開啟 [ `services.msc` 執行]，然後在 [開啟] 方塊中輸入，以開啟 [服務] 管理主控台 `services.msc` 。</span><span class="sxs-lookup"><span data-stu-id="23a49-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="23a49-110">在服務清單的 [**名稱**] 欄中，以滑鼠右鍵按一下 [ **Net.tcp 埠共用服務**]，然後從功能表中選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="23a49-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="23a49-111">若要啟用服務的手動啟動，請在 [**屬性**] 視窗中選取 [**一般**] 索引標籤，然後在 [**啟動類型**] 方塊中選取 [手動]，然後按一下 [套用 **]。**</span><span class="sxs-lookup"><span data-stu-id="23a49-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="23a49-112">若要啟動服務，請在 [服務狀態] 區域中，按一下 [**啟動**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="23a49-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="23a49-113">服務狀態現在應該顯示為「已啟動」。</span><span class="sxs-lookup"><span data-stu-id="23a49-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="23a49-114">若要返回服務清單，請按一下 [**確定]**，然後結束 MMC 主控台。</span><span class="sxs-lookup"><span data-stu-id="23a49-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a49-115">範例</span><span class="sxs-lookup"><span data-stu-id="23a49-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a49-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23a49-116">See also</span></span>

- [<span data-ttu-id="23a49-117">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="23a49-117">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="23a49-118">設定 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="23a49-118">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
