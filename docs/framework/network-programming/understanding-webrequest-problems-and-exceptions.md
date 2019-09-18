---
title: 了解 WebRequest 問題和例外狀況
ms.date: 03/30/2017
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
ms.openlocfilehash: c5712467cdebb854d09cb55c29878cb8b553f271
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047094"
---
# <a name="understanding-webrequest-problems-and-exceptions"></a>了解 WebRequest 問題和例外狀況
<xref:System.Net.WebRequest> 和其衍生的類別 (<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>和 <xref:System.Net.FileWebRequest>) 會擲回例外狀況，以表示發生異常狀況。 有時候這些問題的解決方式並不明顯。  
  
## <a name="solutions"></a>方案  
 請檢查 <xref:System.Net.WebException> 的 <xref:System.Net.WebException.Status%2A> 屬性來判斷問題。 下表顯示數個狀態值和一些可能的解決方式。  
  
|狀態|詳細資料|方案|  
|------------|-------------|--------------|  
|<xref:System.Net.WebExceptionStatus.SendFailure><br /><br /> -或-<br /><br /> <xref:System.Net.WebExceptionStatus.ReceiveFailure>|基礎通訊端有問題。 連接可能已重設。|重新連線，然後重新傳送要求。<br /><br /> 確定已安裝最新的 Service Pack。<br /><br /> 增加 <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=nameWithType> 屬性的值。<br /><br /> 將 <xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=nameWithType> 設定為 `false`。<br /><br /> 使用 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 屬性增加最大連線數目。<br /><br /> 檢查 Proxy 設定。<br /><br /> 如果使用 SSL，請確定伺服器處理序有權存取憑證存放區。<br /><br /> 如果要傳送大量資料，請將 <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A> 設為 `false`。|  
|<xref:System.Net.WebExceptionStatus.TrustFailure>|無法驗證伺服器憑證。|嘗試使用 Internet Explorer 開啟 URI。 解決 IE 顯示的任何安全性警示。 如果您無法解決安全性警示，可以建立憑證原則類別，實作 <xref:System.Net.ICertificatePolicy> 以傳回 `true`，並將它傳遞給 <xref:System.Net.ServicePointManager.CertificatePolicy%2A>。<br /><br /> 請參閱 <https://support.microsoft.com/?id=823177>。<br /><br /> 請確定簽署伺服器憑證之憑證授權單位的憑證，已新增在 Internet Explorer 的 [信任的憑證授權單位] 清單。<br /><br /> 請確定 URL 中的主機名稱符合伺服器憑證上的一般名稱。|  
|<xref:System.Net.WebExceptionStatus.SecureChannelFailure>|在 SSL 交易中發生錯誤，或有憑證問題。|.NET Framework 1.1 版僅支援 SSL 3.0 版。 如果伺服器只使用 TLS 1.0 版或 SSL 2.0 版時，會擲回例外狀況。 升級至 .NET Framework 2.0 版，並設定 <xref:System.Net.ServicePointManager.SecurityProtocol%2A> 以符合伺服器。<br /><br /> 用戶端憑證是由伺服器不信任的憑證授權單位 (CA) 所簽署。 在伺服器上安裝 CA 的憑證。 請參閱 <https://support.microsoft.com/?id=332077>。<br /><br /> 確定已安裝最新的 Service Pack。|  
|<xref:System.Net.WebExceptionStatus.ConnectFailure>|連接失敗。|防火牆或 Proxy 封鎖連線。 修改防火牆或 Proxy 以允許連線。<br /><br /> 藉由呼叫 <xref:System.Net.WebProxy> 建構函式在用戶端應用程式中明確指定 <xref:System.Net.WebProxy> (WebServiceProxyClass.Proxy = new WebProxy([http://server:80](http://server/), true))。<br /><br /> 執行 Filemon 或 Regmon，確保工作者處理序身分識別具有存取 WSPWSP.dll、HKLM\System\CurrentControlSet\Services\DnsCache 或 HKLM\System\CurrentControlSet\Services\WinSock2 的必要權限。|  
|<xref:System.Net.WebExceptionStatus.NameResolutionFailure>|網域名稱服務無法解析主機名稱。|正確設定 Proxy。 請參閱 <https://support.microsoft.com/?id=318140>。<br /><br /> 確定任何已安裝的防毒軟體或防火牆未封鎖連線。|  
|<xref:System.Net.WebExceptionStatus.RequestCanceled>|已呼叫 <xref:System.Net.WebRequest.Abort%2A>，或發生錯誤。|此問題可能起因於用戶端或伺服器上的負載過重。 請降低負載。<br /><br /> 增加 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 設定。<br /><br /> 請參閱 <https://support.microsoft.com/?id=821268> 來修改 Web 服務效能設定。|  
|<xref:System.Net.WebExceptionStatus.ConnectionClosed>|應用程式嘗試寫入已經關閉的通訊端。|用戶端或伺服器已超載。 請降低負載。<br /><br /> 增加 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 設定。<br /><br /> 請參閱 <https://support.microsoft.com/?id=821268> 來修改 Web 服務效能設定。|  
|<xref:System.Net.WebExceptionStatus.MessageLengthLimitExceeded>|已超過對訊息長度所設定的限制 (<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>)。|增加 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> 屬性的值。|  
|<xref:System.Net.WebExceptionStatus.ProxyNameResolutionFailure>|網域名稱服務無法解析 Proxy 主機名稱。|正確設定 Proxy。 請參閱 <https://support.microsoft.com/?id=318140>。<br /><br /> 藉由將 <xref:System.Net.HttpWebRequest.Proxy%2A> 屬性設為 `null`，強制 <xref:System.Net.HttpWebRequest> 不要使用 Proxy。|  
|<xref:System.Net.WebExceptionStatus.ServerProtocolViolation>|伺服器的回應不是有效的 HTTP 回應。 .NET Framework 偵測到伺服器回應不符合 HTTP 1.1 RFC 時，就會發生這個問題。 回應包含不正確的標頭或不正確的標頭分隔符號時，可能會發生這個問題。RFC 2616 定義了 HTTP 1.1 和伺服器回應的有效格式。 如需詳細資訊，請參閱[網際網路工程任務推動小組 (IETF)](https://www.ietf.org/)網站上的 [RFC 2616 - 超文字傳輸通訊協定 -- HTTP/1.1](https://go.microsoft.com/fwlink/?LinkID=147388)。|取得交易的網路追蹤，並檢查回應中的標頭。<br /><br /> 如果您的應用程式需要伺服器回應而不剖析 (這可能是個安全性問題)，請在組態檔中將 `useUnsafeHeaderParsing` 設為 `true`。 請參閱 [\<httpWebRequest> 元素 (網路設定)](../configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.Dns>
