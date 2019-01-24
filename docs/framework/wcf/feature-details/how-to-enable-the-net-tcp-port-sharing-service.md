---
title: HOW TO：啟用 Net.TCP Port Sharing Service
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 490c0d8c4c95eeb2b1cd9b43134720c9e44467ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619593"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="c0fd6-102">HOW TO：啟用 Net.TCP Port Sharing Service</span><span class="sxs-lookup"><span data-stu-id="c0fd6-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="c0fd6-103">Windows Communication Foundation (WCF) 會使用名為 Net.TCP Port Sharing Service 的 Windows 服務，以促進跨多個處理序的 TCP 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="c0fd6-104">此服務已安裝 WCF 的一部分，但服務為了安全起見預設不會啟用，因此必須手動啟用第一次使用之前。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="c0fd6-105">本主題說明如何使用 Microsoft Management Console (MMC) 嵌入式管理單元，來設定 Net TCP Port Sharing Service。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="c0fd6-106">啟用 Net.TCP Port Sharing Service 後，當您以手動方式啟動它時，請參閱[How to:設定 WCF 服務，以使用連接埠共用](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)如需如何將服務設定為使用這項服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="c0fd6-107">如需使用 net.tcp:// 連接埠共用的範例，請參閱 < [Net.TCP Port Sharing 範例](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="c0fd6-108">若要使用 MMC 來啟用 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="c0fd6-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="c0fd6-109">從 開始 功能表中，開啟 服務 管理主控台透過開啟命令提示字元視窗，然後輸入`services.msc`或以開啟 執行，並輸入`services.msc`成 開啟 方塊。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="c0fd6-110">在 **名稱**的服務清單中的資料行上按一下滑鼠右鍵**Net.Tcp Port Sharing Service**，然後選取**屬性**從功能表。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="c0fd6-111">若要啟用的手動啟動的服務，在**屬性**視窗中選取**一般**] 索引標籤，然後在**啟動類型**方塊選取 [手動]，然後再按一下 [ **套用**。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="c0fd6-112">若要啟動服務，服務的 狀態 區域中，按一下**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="c0fd6-113">服務狀態現在應該顯示為「已啟動」。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="c0fd6-114">若要回到服務清單中，按一下**確定**，然後結束 MMC 主控台。</span><span class="sxs-lookup"><span data-stu-id="c0fd6-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0fd6-115">範例</span><span class="sxs-lookup"><span data-stu-id="c0fd6-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0fd6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0fd6-116">See also</span></span>
- [<span data-ttu-id="c0fd6-117">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="c0fd6-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="c0fd6-118">設定 Net.TCP 連接埠共用服務</span><span class="sxs-lookup"><span data-stu-id="c0fd6-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
