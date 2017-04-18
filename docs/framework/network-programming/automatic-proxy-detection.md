---
title: "自動 Proxy 偵測 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "自動 Proxy 偵測"
  - "Web Proxy 自動探索"
  - "Web Proxy"
  - "自動偵測 Proxy"
  - "WebProxy 類別，自動 Proxy 偵測"
  - "Proxy，自動偵測"
  - "網路"
  - "WPAD (Web Proxy 自動探索)"
ms.assetid: fcd9c3bd-93de-4c92-8ff3-837327ad18de
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# 自動 Proxy 偵測
自動 Proxy 偵測是 Web Proxy 伺服器是由系統決定的並用來代表用戶端傳送要求的處理序。  這個功能也稱為「Web Proxy 自動探索」\(Web Proxy Auto\-Discovery，WPAD\)。  當自動 Proxy 偵測啟用，系統會嘗試尋找要傳回一組負責 Proxy 適用於要求的 Proxy 組態指令碼。  如果找到 Proxy 組態指令碼時，指令碼下載，編譯並在本機電腦上執行，因此當 Proxy 資訊、資料流或要求的回應。 <xref:System.Net.WebProxy> 使用一個執行個體的要求時取得。  
  
 自動 Proxy 偵測由 <xref:System.Net.WebProxy> 類別執行，並可使用要求層級設定、使用 Internet Explorer \[**區域網路 \(LAN\)**\] 對話方塊中指定的設定和組態檔中設定。  
  
> [!NOTE]
>  您可以選取 \[**工具**\] 從 Internet Explorer 主功能表然後選取 \[**網際網路選項**\] 顯示 Internet Explorer \[**區域網路 \(LAN\) 設定**\] 對話方塊。  接著，請選取 \[**連接**\] 索引標籤，然後按一下 \[**LAN 設定**\]。  
  
 當自動 Proxy 偵測啟用， <xref:System.Net.WebProxy> 類別會嘗試找出 Proxy 組態指令碼如下所示:  
  
1.  WinINet `InternetQueryOption` 函式用來尋找 Internet Explorer 最近偵測 Proxy 組態指令碼。  
  
2.  如果沒有找到指令碼， <xref:System.Net.WebProxy> 類別使用動態主機設定通訊協定 \(DHCP\) \(DHCP\) 找出指令碼。  DHCP 伺服器可回應的位置 \(主機名稱\) 或指令碼與指令碼的完整 URL。  
  
3.  如果 DHCP 無法識別 WPAD DNS 主機，對於 WPAD 的主應用程式會查詢做為它的名稱或別名。  
  
4.  如果主應用程式未識別，而且 Proxy 組態指令碼的位置是由 Internet Explorer LAN 設定或組態檔中指定，則會使用這個位置。  
  
> [!NOTE]
>  當做獨立的應用程式為或 ASP.NET 中使用 Internet Explorer Proxy 伺服器設定 \(如果有的話\) 叫用的使用者使用。  這些設定可能並不是所有服務應用程式。  
  
 在每個 Proxy connectoid 基礎的配置。  connectoid 位於網路連接對話方塊的項目，而且可以是實體網路裝置 \(資料損毀或 Ethernet 卡\) 或虛擬介面 \(例如在網路裝置\) 的 VPN 連線。  當 connectoid 變更時 \(例如，無線連接變更存取點時，或 VPN 啟用\)， Proxy 偵測演算法再次執行。  
  
 根據預設， Internet Explorer Proxy 設定值用來偵測 Proxy。  如果您的應用程式是以一個非互動式帳戶 \(沒有便利的方式配置 IE Proxy 設定\)，或者，如果您當時 IE 設定要使用 Proxy 設定，您可以建立組態檔來設定 Proxy 以定義的 [\<defaultProxy\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md) 和 [\<proxy\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/proxy-element-network-settings.md) 項目。  
  
 您可以使用類別配合您的需要，空的 <xref:System.Net.WebRequest.Proxy%2A> 如下列程式碼範例所示，針對所建立的需求，您可以在要求層級停用自動 Proxy 偵測層級。  
  
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
  
 沒有 Proxy 使用您的應用程式定義域的預設 Proxy，網址為 <xref:System.Net.WebRequest.DefaultWebProxy%2A> 屬性的要求。  
  
## 請參閱  
 <xref:System.Net.WebProxy>   
 <xref:System.Net.WebRequest>   
 [\<system.net\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)