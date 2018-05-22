---
title: 如何：設定網路追蹤
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 77eb199e5e8bbfb0874f8189a8daa2904b31d48e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-network-tracing"></a>如何：設定網路追蹤
應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。 在執行這個程序之前，請確認已啟用追蹤。 如需啟用追蹤的詳細資訊，請參閱[啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)。  
  
 電腦組態檔 (machine.config) 是儲存在 Windows 安裝目錄中的 %Windir%\Microsoft.NET\Framework 資料夾下。 另外還有一個 machine.config 檔案，位於電腦上所安裝的每個 .NET Framework 版本之 %Windir%\Microsoft.NET\Framework 下的資料夾中 (例如，C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config 或 C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config)。  
  
 您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。  
  
### <a name="to-configure-network-tracing"></a>若要設定網路追蹤  
  
-   將下列各行加入至適當的組態檔中。 下表中會說明這些設定的值和選項。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"  
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。 下表說明這些輸出。  
  
|名稱|輸出來源|  
|----------|-----------------|  
|`System.Net.Sockets`|<xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient> 和 <xref:System.Net.Dns> 類別的一些公用方法|  
|`System.Net`|<xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別的一些公用方法，以及 SSL 偵錯資訊 (無效的憑證、遺失簽發者清單和用戶端憑證錯誤)。|  
|`System.Net.HttpListener`|<xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。|  
|`System.Net.Cache`|`System.Net.Cache` 中的一些私用和內部方法。|  
|`System.Net.Http`|<xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。|  
|`System.Net.WebSockets.WebSocket`|<xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。|  
  
 下表列出的屬性會設定追蹤輸出。  
  
|屬性名稱|屬性值|  
|--------------------|---------------------|  
|`Value`|必要的 <xref:System.String> 屬性。 設定輸出的詳細等級。 合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。<br /><br /> 您必須在 \<switches> 項目的 \<add name> 項目上設定這個屬性，如範例所示。 如果在 \<source> 項目上設定這個屬性，就會擲回例外狀況。|  
|`maxdatasize`|選擇性 <xref:System.Int32> 屬性。 設定每一行追蹤所包含之網路資料的最大位元組數。 預設值為 1024。<br /><br /> 您必須在 \<source> 項目上設定這個屬性，如範例所示。 如果在 \<switches> 項目下的某項目上設定這個屬性，就會擲回例外狀況。|  
|`Tracemode`|選擇性 <xref:System.String> 屬性。 設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。 設定為 `protocolonly` 則只會顯示文字。 預設值是 `includehex`。<br /><br /> 您必須在 \<switches> 項目上設定這個屬性，如範例所示。 如果在 \<source> 項目下的某項目上設定這個屬性，就會擲回例外狀況。|  
  
## <a name="see-also"></a>請參閱  
 [解譯網路追蹤](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [以 .NET Framework 進行網路追蹤](../../../docs/framework/network-programming/network-tracing.md)  
 [啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [檢測和追蹤的簡介](http://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
