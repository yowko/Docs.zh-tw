---
title: "自動 Proxy 偵測"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bbfdb16e284fcd266bcc8ebf41a197733e92ca23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-proxy-detection"></a>自動 Proxy 偵測
自動 Proxy 偵測是一種程序，透過此程序，系統會識別 Web Proxy 伺服器，並用來代表用戶端傳送要求。 這項功能也稱為「Web Proxy 自動探索 (WPAD)」。 啟用自動 Proxy 偵測時，系統會嘗試找出負責傳回可用於要求之這組 Proxy 的 Proxy 組態指令碼。 如果找到 Proxy 組態指令碼，則會在針對使用 <xref:System.Net.WebProxy> 執行個體的要求取得 Proxy 資訊、要求資料流或回應時，在本機電腦上下載、編譯和執行指令碼。  
  
 自動 Proxy 偵測是透過 <xref:System.Net.WebProxy> 類別所執行，而且可以利用要求層級設定、組態檔中的設定，以及使用 Internet Explorer [區域網路 (LAN)] 對話方塊所指定的設定。  
  
> [!NOTE]
>  從 Internet Explorer 主功能表中選取 [工具]，然後選取 [網際網路選項]，即可顯示 Internet Explorer [區域網路 (LAN) 設定] 對話方塊。 接下來，選取 [連線] 索引標籤，然後按一下 [區域網路設定]。  
  
 啟用自動 Proxy 偵測時，<xref:System.Net.WebProxy> 類別會嘗試找到 Proxy 組態指令碼，如下所示：  
  
1.  WinINet `InternetQueryOption` 函式是用來尋找 Internet Explorer 最近偵測到的 Proxy 組態指令碼。  
  
2.  如果找不到指令碼，則 <xref:System.Net.WebProxy> 類別會使用動態主機設定通訊協定 (DHCP) 來找到指令碼。 DHCP 伺服器可以回應指令碼的位置 (主機名稱) 或指令碼的完整 URL。  
  
3.  如果 DHCP 無法識別 WPAD 主機，則會查詢 DNS 中是否有 WPAD 為其名稱或別名的主機。  
  
4.  如果找不到主機，但由 Internet Explorer 區域網路設定或組態檔指定 Proxy 組態指令碼的位置，則會使用此位置。  
  
> [!NOTE]
>  執行為 NT 服務或 ASP.NET 一部分的應用程式會使用叫用使用者的 Internet Explorer Proxy 伺服器設定 (可用時)。 這些設定可能無法用於所有服務應用程式。  
  
 Proxy 是根據 connectoid 所設定。 connectoid 是網路連線對話方塊中的項目，而且可以是實體網路裝置 (數據機或乙太網路卡) 或虛擬介面 (例如透過網路裝置執行的 VPN 連線)。 connectoid 變更時 (例如，無線連線變更存取點，或啟用 VPN)，會再次執行 Proxy 偵測演算法。  
  
 預設會使用 Internet Explorer Proxy 設定來偵測 Proxy。 如果您的應用程式是透過非互動式帳戶執行 (沒有方便的方式可以設定 IE Proxy 設定)，或者您使用的 Proxy 設定與 IE 設定不同，則可以建立已定義 [\<defaultProxy> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 和 [\<roxy> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) 項目的組態檔，來設定 Proxy。  
  
 針對您建立的要求，您可以搭配使用 Null <xref:System.Net.WebRequest.Proxy%2A> 與您的要求來停用要求層級的自動 Proxy 偵測，如下列程式碼範例所示。  
  
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
  
 沒有 Proxy 的要求會使用應用程式定義域的預設 Proxy，而其可在 <xref:System.Net.WebRequest.DefaultWebProxy%2A> 屬性中取得。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.WebRequest>  
 [\<system.Net> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)
