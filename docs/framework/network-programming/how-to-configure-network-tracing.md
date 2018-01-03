---
title: "如何：設定網路追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4a6b277b2676409bebc059637daca5681b853f03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="310e8-102">如何：設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="310e8-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="310e8-103">應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。</span><span class="sxs-lookup"><span data-stu-id="310e8-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="310e8-104">在執行這個程序之前，請確認已啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="310e8-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="310e8-105">如需啟用追蹤的詳細資訊，請參閱[啟用網路追蹤](../../../docs/framework/network-programming/enabling-network-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="310e8-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="310e8-106">電腦組態檔 (machine.config) 是儲存在 Windows 安裝目錄中的 %Windir%\Microsoft.NET\Framework 資料夾下。</span><span class="sxs-lookup"><span data-stu-id="310e8-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="310e8-107">（例如，C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config 或 C:\Windows\ 在電腦上安裝的.NET Framework 的每個版本的 %Windir%\Microsoft.NET\Framework 資料夾中沒有一個 machine.config 檔案Microsoft.NET\Framework64\v4.0.30319\Config\machine.config。)。</span><span class="sxs-lookup"><span data-stu-id="310e8-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="310e8-108">您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="310e8-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="310e8-109">若要設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="310e8-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="310e8-110">將下列各行加入至適當的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="310e8-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="310e8-111">下表中會說明這些設定的值和選項。</span><span class="sxs-lookup"><span data-stu-id="310e8-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="310e8-112">當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="310e8-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="310e8-113">下表說明這些輸出。</span><span class="sxs-lookup"><span data-stu-id="310e8-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="310e8-114">名稱</span><span class="sxs-lookup"><span data-stu-id="310e8-114">Name</span></span>|<span data-ttu-id="310e8-115">輸出來源</span><span class="sxs-lookup"><span data-stu-id="310e8-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="310e8-116"><xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient> 和 <xref:System.Net.Dns> 類別的一些公用方法</span><span class="sxs-lookup"><span data-stu-id="310e8-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="310e8-117"><xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別的一些公用方法，以及 SSL 偵錯資訊 (無效的憑證、遺失簽發者清單和用戶端憑證錯誤)。</span><span class="sxs-lookup"><span data-stu-id="310e8-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="310e8-118"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="310e8-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="310e8-119">`System.Net.Cache` 中的一些私用和內部方法。</span><span class="sxs-lookup"><span data-stu-id="310e8-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="310e8-120"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="310e8-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="310e8-121"><xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="310e8-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="310e8-122">下表列出的屬性會設定追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="310e8-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="310e8-123">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="310e8-123">Attribute name</span></span>|<span data-ttu-id="310e8-124">屬性值</span><span class="sxs-lookup"><span data-stu-id="310e8-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="310e8-125">必要的 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="310e8-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="310e8-126">設定輸出的詳細等級。</span><span class="sxs-lookup"><span data-stu-id="310e8-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="310e8-127">合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。</span><span class="sxs-lookup"><span data-stu-id="310e8-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="310e8-128">您必須在 \<switches> 項目的 \<add name> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="310e8-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="310e8-129">如果在 \<source> 項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="310e8-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="310e8-130">選擇性 <xref:System.Int32> 屬性。</span><span class="sxs-lookup"><span data-stu-id="310e8-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="310e8-131">設定每一行追蹤所包含之網路資料的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="310e8-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="310e8-132">預設值為 1024。</span><span class="sxs-lookup"><span data-stu-id="310e8-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="310e8-133">您必須在 \<source> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="310e8-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="310e8-134">如果在 \<switches> 項目下的某項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="310e8-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="310e8-135">選擇性 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="310e8-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="310e8-136">設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。</span><span class="sxs-lookup"><span data-stu-id="310e8-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="310e8-137">設定為 `protocolonly` 則只會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="310e8-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="310e8-138">預設值是 `includehex`。</span><span class="sxs-lookup"><span data-stu-id="310e8-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="310e8-139">您必須在 \<switches> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="310e8-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="310e8-140">如果在 \<source> 項目下的某項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="310e8-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="310e8-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="310e8-141">See Also</span></span>  
 [<span data-ttu-id="310e8-142">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="310e8-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="310e8-143">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="310e8-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="310e8-144">啟用網路追蹤</span><span class="sxs-lookup"><span data-stu-id="310e8-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="310e8-145">檢測和追蹤的簡介</span><span class="sxs-lookup"><span data-stu-id="310e8-145">Introduction to Instrumentation and Tracing</span></span>](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
