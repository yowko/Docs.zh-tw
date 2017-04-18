---
title: "了解 WebRequest 問題和例外狀況 | Microsoft Docs"
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
ms.assetid: 74a361a5-e912-42d3-8f2e-8e9a96880a2b
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# 了解 WebRequest 問題和例外狀況
<xref:System.Net.WebRequest> 和它的衍生類別 \(<xref:System.Net.HttpWebRequest>、 <xref:System.Net.FtpWebRequest>和 <xref:System.Net.FileWebRequest>\) 擲回例外狀況表示一個異常條件。  有時候這些問題的解決方式不會很明顯。  
  
## 方案  
 檢查 <xref:System.Net.WebException> 的 <xref:System.Net.WebException.Status%2A> 屬性判斷問題。  下表顯示幾個狀態值和可能的解決方式。  
  
|狀態|詳細資訊|解決方案|  
|--------|----------|----------|  
|<xref:System.Net.WebExceptionStatus><br /><br /> \-或\-<br /><br /> <xref:System.Net.WebExceptionStatus>|取得基礎通訊端的問題。  連接會重設。|重新連接並重新傳送要求。<br /><br /> 判斷最新的 Service Pack 安裝。<br /><br /> 將 <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A?displayProperty=fullName> 屬性的值。<br /><br /> 將 \[<xref:System.Net.HttpWebRequest.KeepAlive%2A?displayProperty=fullName>\] 設為 \[`false`\]。<br /><br /> 將連接最大數目。 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 屬性的。<br /><br /> 檢查 Proxy 組態。<br /><br /> 如果使用 SSL，請確定伺服器處理序擁有存取權限的憑證存放區。<br /><br /> 如果傳送大量的資料，設定為 <xref:System.Net.HttpWebRequest.AllowWriteStreamBuffering%2A>`false`。|  
|<xref:System.Net.WebExceptionStatus>|伺服器憑證無法驗證。|使用 Internet Explorer，嘗試開啟 URI。  剖析 IE 顯示的所有安全性警示。  如果無法解決安全性警示，則您可以建立實作 <xref:System.Net.ICertificatePolicy> 傳回 `true`，並將它傳遞至 <xref:System.Net.ServicePointManager.CertificatePolicy%2A>的憑證原則類別。<br /><br /> 請 [http:\/\/support.microsoft.com\/?id\=823177](http://go.microsoft.com/fwlink/?LinkID=179653)參閱。<br /><br /> 確定簽署伺服器憑證的憑證授權單位的憑證加入至 Internet Explorer 中的信任憑證授權單位清單。<br /><br /> 請確定在 URL 的主機名稱符合伺服器憑證的通用名稱。|  
|<xref:System.Net.WebExceptionStatus>|錯誤在 SSL 交易發生，或是有憑證問題。|僅限 .NET Framework 1.1 版支援 SSL 3.0 版。  如果伺服器使用 TLS SSL 1.0 版或 2.0 版，就會擲回例外狀況。  與 .NET Framework 2.0 版的升級和集合符合伺服器的 <xref:System.Net.ServicePointManager.SecurityProtocol%2A> 。<br /><br /> 用戶端憑證是由伺服器不信任的憑證授權單位 \(CA\) 簽署。  在伺服器上安裝 CA 憑證。  請 [http:\/\/support.microsoft.com\/?id\=332077](http://go.microsoft.com/fwlink/?LinkID=179654)參閱。<br /><br /> 確定您有最新的 Service Pack 安裝。|  
|<xref:System.Net.WebExceptionStatus>|連接失敗。|防火牆或 Proxy 阻斷連接。  修改此防火牆或 Proxy 允許連接。<br /><br /> 請呼叫 <xref:System.Net.WebProxy> 建構函式明確地將用戶端應用程式的 <xref:System.Net.WebProxy> \(WebServiceProxyClass.Proxy \= new WebProxy true \([http:\/\/server:80](http://server/)，\)\)。<br /><br /> 執行 Filemon 或 Regmon 確保背景工作處理序識別具有必要的使用權限存取 WSPWSP.dll、HKLM \\ System \\ CurrentControlSet \\ Services \\ DnsCache 或 HKLM \\ System \\ CurrentControlSet \\ Services \\ WinSock2。|  
|<xref:System.Net.WebExceptionStatus>|網域名稱服務無法解析主機名稱。|正確設定 Proxy。  請 [http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655)參閱。<br /><br /> 確定任何安裝的防毒軟體或防火牆並未封鎖連接。|  
|<xref:System.Net.WebExceptionStatus>|<xref:System.Net.WebRequest.Abort%2A> 呼叫，或發生錯誤。|這個問題可能是在用戶端或伺服器的重度負載產生。  減少載入。<br /><br /> 將 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 設定。<br /><br /> 請 [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) 參閱修改 Web 服務效能設定。|  
|<xref:System.Net.WebExceptionStatus>|應用程式嘗試寫入已經關閉的通訊端寫入。|用戶端或伺服器上的多載。  減少載入。<br /><br /> 將 <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> 設定。<br /><br /> 請 [http:\/\/support.microsoft.com\/?id\=821268](http://go.microsoft.com/fwlink/?LinkID=179656) 參閱修改 Web 服務效能設定。|  
|<xref:System.Net.WebExceptionStatus>|在訊息長度為的 \(<xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>\)限制超過。|將 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A> 屬性的值。|  
|<xref:System.Net.WebExceptionStatus>|網域名稱服務無法解析 Proxy 主機名稱。|正確設定 Proxy。  請 [http:\/\/support.microsoft.com\/?id\=318140](http://go.microsoft.com/fwlink/?LinkID=179655)參閱。<br /><br /> 不要強制 <xref:System.Net.HttpWebRequest> 藉由設定 <xref:System.Net.HttpWebRequest.Proxy%2A> 屬性使用 Proxy `null`。|  
|<xref:System.Net.WebExceptionStatus>|來自伺服器的回應不是有效的 HTTP 回應。  這個問題發生，而 .NET Framework 偵測伺服器回應 HTTP 不符合 RFC 1.1。  這個問題，可能會發生在回應包含無效的標頭時或無效的標頭 delimiters.RFC 2616 定義 HTTP 1.1 和 HTTP 回應的有效格式從伺服器。  如需詳細資訊， [http:\/\/www.ietf.org](http://go.microsoft.com/fwlink/?LinkID=147388)請參閱|取得交易的網路追蹤並檢查這個回應關聯的標頭。<br /><br /> 如果您的應用程式需要伺服器回應，而不解決 \(這可能是安全性問題\)，將 `useUnsafeHeaderParsing` 至組態檔的 `true` 。  請參閱 [\<httpWebRequest\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)。|  
  
## 請參閱  
 <xref:System.Net.HttpWebRequest>   
 <xref:System.Net.HttpWebResponse>   
 <xref:System.Net.Dns>