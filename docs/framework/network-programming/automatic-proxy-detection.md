---
title: 自動 Proxy 偵測
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic proxy detections
- Web Proxy Auto-Discovery
- Web proxy
- detecting proxies automatically
- WebProxy class, automatic proxy detections
- proxies, automatically detecting
- network
- WPAD (Web Proxy Auto-Discovery)
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: acb14d8785a01d98d56233b8eb942f9bc4675f63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394877"
---
# <a name="automatic-proxy-detection"></a><span data-ttu-id="b105a-102">自動 Proxy 偵測</span><span class="sxs-lookup"><span data-stu-id="b105a-102">Automatic Proxy Detection</span></span>
<span data-ttu-id="b105a-103">自動 Proxy 偵測是一種程序，透過此程序，系統會識別 Web Proxy 伺服器，並用來代表用戶端傳送要求。</span><span class="sxs-lookup"><span data-stu-id="b105a-103">Automatic proxy detection is a process by which a Web proxy server is identified by the system and used to send requests on behalf of the client.</span></span> <span data-ttu-id="b105a-104">這項功能也稱為「Web Proxy 自動探索 (WPAD)」。</span><span class="sxs-lookup"><span data-stu-id="b105a-104">This feature is also known as Web Proxy Auto-Discovery (WPAD).</span></span> <span data-ttu-id="b105a-105">啟用自動 Proxy 偵測時，系統會嘗試找出負責傳回可用於要求之這組 Proxy 的 Proxy 組態指令碼。</span><span class="sxs-lookup"><span data-stu-id="b105a-105">When automatic proxy detection is enabled, the system attempts to locate a proxy configuration script that is responsible for returning the set of proxies that can be used for the request.</span></span> <span data-ttu-id="b105a-106">如果找到 Proxy 組態指令碼，則會在針對使用 <xref:System.Net.WebProxy> 執行個體的要求取得 Proxy 資訊、要求資料流或回應時，在本機電腦上下載、編譯和執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="b105a-106">If the proxy configuration script is found, the script is downloaded, compiled, and run on the local computer when proxy information, the request stream, or the response is obtained for a request that uses a <xref:System.Net.WebProxy> instance.</span></span>  
  
 <span data-ttu-id="b105a-107">自動 Proxy 偵測是透過 <xref:System.Net.WebProxy> 類別所執行，而且可以利用要求層級設定、組態檔中的設定，以及使用 Internet Explorer [區域網路 (LAN)] 對話方塊所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="b105a-107">Automatic proxy detection is performed by the <xref:System.Net.WebProxy> class and can employ request-level settings, settings in configuration files, and settings specified using the Internet Explorer **Local Area Network (LAN)** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b105a-108">從 Internet Explorer 主功能表中選取 [工具]，然後選取 [網際網路選項]，即可顯示 Internet Explorer [區域網路 (LAN) 設定] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b105a-108">You can display the Internet Explorer **Local Area Network (LAN) Settings** dialog box by selecting **Tools** from the Internet Explorer main menu and then selecting **Internet Options**.</span></span> <span data-ttu-id="b105a-109">接下來，選取 [連線] 索引標籤，然後按一下 [區域網路設定]。</span><span class="sxs-lookup"><span data-stu-id="b105a-109">Next, select the **Connections** tab, and click **LAN Settings**.</span></span>  
  
 <span data-ttu-id="b105a-110">啟用自動 Proxy 偵測時，<xref:System.Net.WebProxy> 類別會嘗試找到 Proxy 組態指令碼，如下所示：</span><span class="sxs-lookup"><span data-stu-id="b105a-110">When automatic proxy detection is enabled, the <xref:System.Net.WebProxy> class attempts to locate the proxy configuration script as follows:</span></span>  
  
1.  <span data-ttu-id="b105a-111">WinINet `InternetQueryOption` 函式是用來尋找 Internet Explorer 最近偵測到的 Proxy 組態指令碼。</span><span class="sxs-lookup"><span data-stu-id="b105a-111">The WinINet `InternetQueryOption` function is used to locate the proxy configuration script most recently detected by Internet Explorer.</span></span>  
  
2.  <span data-ttu-id="b105a-112">如果找不到指令碼，則 <xref:System.Net.WebProxy> 類別會使用動態主機設定通訊協定 (DHCP) 來找到指令碼。</span><span class="sxs-lookup"><span data-stu-id="b105a-112">If the script is not located, the <xref:System.Net.WebProxy> class uses the Dynamic Host Configuration Protocol (DHCP) to locate the script.</span></span> <span data-ttu-id="b105a-113">DHCP 伺服器可以回應指令碼的位置 (主機名稱) 或指令碼的完整 URL。</span><span class="sxs-lookup"><span data-stu-id="b105a-113">The DHCP server can respond either with the location (host name) of the script or with the full URL for the script.</span></span>  
  
3.  <span data-ttu-id="b105a-114">如果 DHCP 無法識別 WPAD 主機，則會查詢 DNS 中是否有 WPAD 為其名稱或別名的主機。</span><span class="sxs-lookup"><span data-stu-id="b105a-114">If DHCP does not identify the WPAD host, DNS is queried for a host with WPAD as its name or alias.</span></span>  
  
4.  <span data-ttu-id="b105a-115">如果找不到主機，但由 Internet Explorer 區域網路設定或組態檔指定 Proxy 組態指令碼的位置，則會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="b105a-115">If the host is not identified and the location of a proxy configuration script is specified by the Internet Explorer LAN settings or a configuration file, this location is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b105a-116">執行為 NT 服務或 ASP.NET 一部分的應用程式會使用叫用使用者的 Internet Explorer Proxy 伺服器設定 (可用時)。</span><span class="sxs-lookup"><span data-stu-id="b105a-116">Applications running as an NT Service or as part of ASP.NET use the Internet Explorer proxy server settings (if available) of the invoking user.</span></span> <span data-ttu-id="b105a-117">這些設定可能無法用於所有服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="b105a-117">These settings may not be available for all service applications.</span></span>  
  
 <span data-ttu-id="b105a-118">Proxy 是根據 connectoid 所設定。</span><span class="sxs-lookup"><span data-stu-id="b105a-118">Proxies are configured on a per-connectoid basis.</span></span> <span data-ttu-id="b105a-119">connectoid 是網路連線對話方塊中的項目，而且可以是實體網路裝置 (數據機或乙太網路卡) 或虛擬介面 (例如透過網路裝置執行的 VPN 連線)。</span><span class="sxs-lookup"><span data-stu-id="b105a-119">A connectoid is an item in the network connection dialog, and can be a physical network device (a modem or Ethernet card) or a virtual interface (such as a VPN connection running over a network device).</span></span> <span data-ttu-id="b105a-120">connectoid 變更時 (例如，無線連線變更存取點，或啟用 VPN)，會再次執行 Proxy 偵測演算法。</span><span class="sxs-lookup"><span data-stu-id="b105a-120">When a connectoid changes (for example, a wireless connection changes an access point, or a VPN is enabled), the proxy detection algorithm is run again.</span></span>  
  
 <span data-ttu-id="b105a-121">預設會使用 Internet Explorer Proxy 設定來偵測 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b105a-121">By default, the Internet Explorer proxy settings are used to detect the proxy.</span></span> <span data-ttu-id="b105a-122">如果您的應用程式是透過非互動式帳戶執行 (沒有方便的方式可以設定 IE Proxy 設定)，或者您使用的 Proxy 設定與 IE 設定不同，則可以建立已定義 [\<defaultProxy> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 和 [\<roxy> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) 項目的組態檔，來設定 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b105a-122">If your application is running under a non-interactive account (without a convenient way to configure IE proxy settings), or if you want to use proxy settings different than the IE settings, you can configure your proxy by creating a configuration file with the [\<defaultProxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) and [\<proxy> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) elements defined.</span></span>  
  
 <span data-ttu-id="b105a-123">針對您建立的要求，您可以搭配使用 Null <xref:System.Net.WebRequest.Proxy%2A> 與您的要求來停用要求層級的自動 Proxy 偵測，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="b105a-123">For requests that you create, you can disable automatic proxy detection at the request level by using a null <xref:System.Net.WebRequest.Proxy%2A> with your request, as shown in the following code example.</span></span>  
  
```csharp  
public static void DisableForMyRequest (Uri resource)  
{  
    WebRequest request = WebRequest.Create (resource);  
    request.Proxy = null;  
    WebResponse response = request.GetResponse ();  
}  
```  
  
```vb  
Public Shared Sub DisableForMyRequest(ByVal resource As Uri)  
    Dim request As WebRequest = WebRequest.Create(resource)  
    request.Proxy = Nothing  
    Dim response As WebResponse = request.GetResponse()  
    End Sub   
```  
  
 <span data-ttu-id="b105a-124">沒有 Proxy 的要求會使用應用程式定義域的預設 Proxy，而其可在 <xref:System.Net.WebRequest.DefaultWebProxy%2A> 屬性中取得。</span><span class="sxs-lookup"><span data-stu-id="b105a-124">Requests that do not have a proxy use your application domain's default proxy, which is available in the <xref:System.Net.WebRequest.DefaultWebProxy%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b105a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="b105a-125">See Also</span></span>  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="b105a-126">\<system.Net> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="b105a-126">\<system.Net> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
