---
title: 作法：設定網路追蹤
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
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048374"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="13fb0-102">HOW TO：設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="13fb0-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="13fb0-103">應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。</span><span class="sxs-lookup"><span data-stu-id="13fb0-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="13fb0-104">在執行這個程序之前，請確認已啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="13fb0-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="13fb0-105">如需啟用追蹤的詳細資訊，請參閱[啟用網路追蹤](enabling-network-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="13fb0-105">For information about enabling tracing, see [Enabling Network Tracing](enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="13fb0-106">電腦組態檔 (machine.config) 是儲存在 Windows 安裝目錄中的 %Windir%\Microsoft.NET\Framework 資料夾下。</span><span class="sxs-lookup"><span data-stu-id="13fb0-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="13fb0-107">另外還有一個 machine.config 檔案，位於電腦上所安裝的每個 .NET Framework 版本之 %Windir%\Microsoft.NET\Framework 下的資料夾中 (例如，C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config 或 C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config)。</span><span class="sxs-lookup"><span data-stu-id="13fb0-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="13fb0-108">您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="13fb0-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="13fb0-109">若要設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="13fb0-109">To configure network tracing</span></span>  
  
- <span data-ttu-id="13fb0-110">將下列各行加入至適當的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="13fb0-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="13fb0-111">下表中會說明這些設定的值和選項。</span><span class="sxs-lookup"><span data-stu-id="13fb0-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
            traceOutputOptions="ProcessId, DateTime" 
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 <span data-ttu-id="13fb0-112">當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="13fb0-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="13fb0-113">下表說明這些輸出。</span><span class="sxs-lookup"><span data-stu-id="13fb0-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="13fb0-114">名稱</span><span class="sxs-lookup"><span data-stu-id="13fb0-114">Name</span></span>|<span data-ttu-id="13fb0-115">輸出來源</span><span class="sxs-lookup"><span data-stu-id="13fb0-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="13fb0-116"><xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>、<xref:System.Net.Sockets.TcpClient> 和 <xref:System.Net.Dns> 類別的一些公用方法</span><span class="sxs-lookup"><span data-stu-id="13fb0-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="13fb0-117"><xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>、<xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別的一些公用方法，以及 SSL 偵錯資訊 (無效的憑證、遺失簽發者清單和用戶端憑證錯誤)。</span><span class="sxs-lookup"><span data-stu-id="13fb0-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="13fb0-118"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="13fb0-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="13fb0-119">`System.Net.Cache` 中的一些私用和內部方法。</span><span class="sxs-lookup"><span data-stu-id="13fb0-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="13fb0-120"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="13fb0-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="13fb0-121"><xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="13fb0-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="13fb0-122">下表列出的屬性會設定追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="13fb0-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="13fb0-123">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="13fb0-123">Attribute name</span></span>|<span data-ttu-id="13fb0-124">屬性值</span><span class="sxs-lookup"><span data-stu-id="13fb0-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="13fb0-125">必要的 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13fb0-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="13fb0-126">設定輸出的詳細等級。</span><span class="sxs-lookup"><span data-stu-id="13fb0-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="13fb0-127">合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。</span><span class="sxs-lookup"><span data-stu-id="13fb0-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="13fb0-128">您必須在 \<switches> 項目的 \<add name> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="13fb0-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="13fb0-129">如果在 \<source> 項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="13fb0-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="13fb0-130">選擇性 <xref:System.Int32> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13fb0-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="13fb0-131">設定每一行追蹤所包含之網路資料的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="13fb0-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="13fb0-132">預設值為 1024。</span><span class="sxs-lookup"><span data-stu-id="13fb0-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="13fb0-133">您必須在 \<source> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="13fb0-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="13fb0-134">如果在 \<switches> 項目下的某項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="13fb0-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="13fb0-135">選擇性 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13fb0-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="13fb0-136">設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。</span><span class="sxs-lookup"><span data-stu-id="13fb0-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="13fb0-137">設定為 `protocolonly` 則只會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="13fb0-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="13fb0-138">預設值是 `includehex`。</span><span class="sxs-lookup"><span data-stu-id="13fb0-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="13fb0-139">您必須在 \<switches> 項目上設定這個屬性，如範例所示。</span><span class="sxs-lookup"><span data-stu-id="13fb0-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="13fb0-140">如果在 \<source> 項目下的某項目上設定這個屬性，就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="13fb0-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13fb0-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13fb0-141">See also</span></span>

- [<span data-ttu-id="13fb0-142">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="13fb0-142">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="13fb0-143">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="13fb0-143">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="13fb0-144">啟用網路追蹤</span><span class="sxs-lookup"><span data-stu-id="13fb0-144">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="13fb0-145">追蹤和檢測應用程式</span><span class="sxs-lookup"><span data-stu-id="13fb0-145">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
