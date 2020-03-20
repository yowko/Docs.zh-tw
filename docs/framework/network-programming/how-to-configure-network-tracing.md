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
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040648"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="29d90-102">如何：配置網路跟蹤</span><span class="sxs-lookup"><span data-stu-id="29d90-102">How to: Configure network tracing</span></span>

<span data-ttu-id="29d90-103">應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。</span><span class="sxs-lookup"><span data-stu-id="29d90-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="29d90-104">在執行這個程序之前，請確認已啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="29d90-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="29d90-105">有關詳細資訊，請參閱[啟用網路跟蹤](enabling-network-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="29d90-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="29d90-106">電腦設定檔 *，電腦.config*，存儲在 *%windir%\Microsoft.NET_Framework*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="29d90-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="29d90-107">*在 %windir%_Microsoft.NET_Framework*的資料夾中，對於電腦上安裝的每個版本的 .NET Framework，有一個單獨的*電腦.config*檔，例如：</span><span class="sxs-lookup"><span data-stu-id="29d90-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="29d90-108">*C：_WINDOWS_微軟.NET_Framework_v2.0.50727_機器。*</span><span class="sxs-lookup"><span data-stu-id="29d90-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="29d90-109">*C：_WINDOWS_微軟.NET_Framework64_v4.0.30319\機器。*</span><span class="sxs-lookup"><span data-stu-id="29d90-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="29d90-110">您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="29d90-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="29d90-111">配置網路跟蹤</span><span class="sxs-lookup"><span data-stu-id="29d90-111">Configure network tracing</span></span>

<span data-ttu-id="29d90-112">要配置網路跟蹤，請將以下行添加到相應的設定檔。</span><span class="sxs-lookup"><span data-stu-id="29d90-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="29d90-113">下表中會說明這些設定的值和選項。</span><span class="sxs-lookup"><span data-stu-id="29d90-113">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="29d90-114">從方法跟蹤輸出</span><span class="sxs-lookup"><span data-stu-id="29d90-114">Trace output from methods</span></span>

<span data-ttu-id="29d90-115">當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="29d90-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="29d90-116">下表描述了輸出：</span><span class="sxs-lookup"><span data-stu-id="29d90-116">The following table describes the output:</span></span>

|<span data-ttu-id="29d90-117">名稱</span><span class="sxs-lookup"><span data-stu-id="29d90-117">Name</span></span>|<span data-ttu-id="29d90-118">輸出來源</span><span class="sxs-lookup"><span data-stu-id="29d90-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="29d90-119"><xref:System.Net.Sockets.Socket>、<xref:System.Net.Sockets.TcpListener>和<xref:System.Net.Sockets.TcpClient><xref:System.Net.Dns>類的一些公共方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="29d90-120"><xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpWebResponse>和<xref:System.Net.FtpWebRequest>類以及<xref:System.Net.FtpWebResponse>SSL 調試資訊（無效證書、缺少頒發者清單和用戶端憑證錯誤）的某些公共方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="29d90-121"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="29d90-122">`System.Net.Cache` 中的一些私用和內部方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="29d90-123"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="29d90-124"><xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="29d90-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="29d90-125">跟蹤輸出屬性</span><span class="sxs-lookup"><span data-stu-id="29d90-125">Trace output attributes</span></span>

<span data-ttu-id="29d90-126">下表中列出的屬性配置跟蹤輸出：</span><span class="sxs-lookup"><span data-stu-id="29d90-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="29d90-127">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="29d90-127">Attribute name</span></span>|<span data-ttu-id="29d90-128">屬性值</span><span class="sxs-lookup"><span data-stu-id="29d90-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="29d90-129">必要的 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="29d90-130">設定輸出的詳細等級。</span><span class="sxs-lookup"><span data-stu-id="29d90-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="29d90-131">合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。</span><span class="sxs-lookup"><span data-stu-id="29d90-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="29d90-132">必須在**交換器**元素的**添加**元素上設置此屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="29d90-133">如果在**源**元素上設置了此屬性，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="29d90-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="29d90-134">範例： `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="29d90-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="29d90-135">選擇性 <xref:System.Int32> 屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="29d90-136">設定每一行追蹤所包含之網路資料的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="29d90-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="29d90-137">預設值為 1024。</span><span class="sxs-lookup"><span data-stu-id="29d90-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="29d90-138">必須在**源**元素上設置此屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="29d90-139">如果在**交換器**元素下的元素上設置此屬性，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="29d90-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="29d90-140">範例： `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="29d90-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="29d90-141">選擇性 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="29d90-142">設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。</span><span class="sxs-lookup"><span data-stu-id="29d90-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="29d90-143">設定為 `protocolonly` 則只會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="29d90-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="29d90-144">預設值是 `includehex`。</span><span class="sxs-lookup"><span data-stu-id="29d90-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="29d90-145">必須在**源**元素上設置此屬性。</span><span class="sxs-lookup"><span data-stu-id="29d90-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="29d90-146">如果在**交換器**元素下的元素上設置此屬性，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="29d90-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="29d90-147">範例： `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="29d90-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="29d90-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29d90-148">See also</span></span>

- [<span data-ttu-id="29d90-149">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="29d90-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="29d90-150">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="29d90-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="29d90-151">啟用網路追蹤</span><span class="sxs-lookup"><span data-stu-id="29d90-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="29d90-152">追蹤和稽核應用程式</span><span class="sxs-lookup"><span data-stu-id="29d90-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
