---
title: 如何：設定網路追蹤
description: 瞭解如何在電腦設定檔或應用程式佈建檔中設定網路追蹤。 應用程式佈建檔的優先順序較高。
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
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502557"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="fe511-104">如何：設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="fe511-104">How to: Configure network tracing</span></span>

<span data-ttu-id="fe511-105">應用程式或電腦組態檔都會保存可決定網路追蹤格式和內容的設定。</span><span class="sxs-lookup"><span data-stu-id="fe511-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="fe511-106">在執行這個程序之前，請確認已啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="fe511-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="fe511-107">如需詳細資訊，請參閱[啟用網路追蹤](enabling-network-tracing.md)。</span><span class="sxs-lookup"><span data-stu-id="fe511-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="fe511-108">電腦配置*檔 machine.config 會*儲存在 *%windir%\Microsoft.NET\Framework*資料夾中。</span><span class="sxs-lookup"><span data-stu-id="fe511-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="fe511-109">針對電腦上安裝的每個 .NET Framework 版本， *%windir%\Microsoft.NET\Framework*下的資料夾中有個別的*machine.config*檔案，例如：</span><span class="sxs-lookup"><span data-stu-id="fe511-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="fe511-110">*C：\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="fe511-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="fe511-111">*C：\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="fe511-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="fe511-112">您也可以在應用程式的組態檔中進行這些設定，它的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="fe511-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="fe511-113">設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="fe511-113">Configure network tracing</span></span>

<span data-ttu-id="fe511-114">若要設定網路追蹤，請將下列幾行新增至適當的設定檔。</span><span class="sxs-lookup"><span data-stu-id="fe511-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="fe511-115">下表中會說明這些設定的值和選項。</span><span class="sxs-lookup"><span data-stu-id="fe511-115">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="fe511-116">方法的追蹤輸出</span><span class="sxs-lookup"><span data-stu-id="fe511-116">Trace output from methods</span></span>

<span data-ttu-id="fe511-117">當您將名稱加入至 `<switches>` 區塊時，追蹤輸出就會包括來自與該名稱相關的某些方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="fe511-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="fe511-118">下表描述輸出：</span><span class="sxs-lookup"><span data-stu-id="fe511-118">The following table describes the output:</span></span>

|<span data-ttu-id="fe511-119">Name</span><span class="sxs-lookup"><span data-stu-id="fe511-119">Name</span></span>|<span data-ttu-id="fe511-120">輸出來源</span><span class="sxs-lookup"><span data-stu-id="fe511-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="fe511-121"><xref:System.Net.Sockets.Socket>、、 <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.TcpClient> 和類別的一些公用方法 <xref:System.Net.Dns> 。</span><span class="sxs-lookup"><span data-stu-id="fe511-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="fe511-122">、、和類別的一些公用方法 <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> ，以及 SSL 的調試資訊（不正確憑證、缺少的簽發者清單，以及用戶端憑證錯誤）。</span><span class="sxs-lookup"><span data-stu-id="fe511-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="fe511-123"><xref:System.Net.HttpListener>、<xref:System.Net.HttpListenerRequest> 和 <xref:System.Net.HttpListenerResponse> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="fe511-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="fe511-124">`System.Net.Cache` 中的一些私用和內部方法。</span><span class="sxs-lookup"><span data-stu-id="fe511-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="fe511-125"><xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.DelegatingHandler>、<xref:System.Net.Http.HttpClientHandler>、<xref:System.Net.Http.HttpMessageHandler>、<xref:System.Net.Http.MessageProcessingHandler> 和 <xref:System.Net.Http.WebRequestHandler> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="fe511-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="fe511-126"><xref:System.Net.WebSockets.ClientWebSocket> 和 <xref:System.Net.WebSockets.WebSocket> 類別的一些公用方法。</span><span class="sxs-lookup"><span data-stu-id="fe511-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="fe511-127">追蹤輸出屬性</span><span class="sxs-lookup"><span data-stu-id="fe511-127">Trace output attributes</span></span>

<span data-ttu-id="fe511-128">下表所列的屬性會設定追蹤輸出：</span><span class="sxs-lookup"><span data-stu-id="fe511-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="fe511-129">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="fe511-129">Attribute name</span></span>|<span data-ttu-id="fe511-130">屬性值</span><span class="sxs-lookup"><span data-stu-id="fe511-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="fe511-131">必要的 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fe511-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="fe511-132">設定輸出的詳細等級。</span><span class="sxs-lookup"><span data-stu-id="fe511-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="fe511-133">合法值為 `Critical`、`Error`、`Verbose`、`Warning` 和 `Information`。</span><span class="sxs-lookup"><span data-stu-id="fe511-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="fe511-134">這個屬性必須在 switch 元素的**add** **元素上**設定。</span><span class="sxs-lookup"><span data-stu-id="fe511-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="fe511-135">如果在**來源**元素上設定此屬性，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe511-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="fe511-136">範例： `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="fe511-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="fe511-137">選擇性 <xref:System.Int32> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fe511-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="fe511-138">設定每一行追蹤所包含之網路資料的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="fe511-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="fe511-139">預設值為 1024。</span><span class="sxs-lookup"><span data-stu-id="fe511-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="fe511-140">必須在**來源**元素上設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fe511-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="fe511-141">如果**在 switch 元素下**的專案上設定這個屬性，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe511-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="fe511-142">範例： `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="fe511-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="fe511-143">選擇性 <xref:System.String> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fe511-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="fe511-144">設定為 `includehex` 以便使用十六進位和文字格式來顯示通訊協定追蹤。</span><span class="sxs-lookup"><span data-stu-id="fe511-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="fe511-145">設定為 `protocolonly` 則只會顯示文字。</span><span class="sxs-lookup"><span data-stu-id="fe511-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="fe511-146">預設值為 `includehex`。</span><span class="sxs-lookup"><span data-stu-id="fe511-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="fe511-147">必須在**來源**元素上設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="fe511-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="fe511-148">如果**在 switch 元素下**的專案上設定這個屬性，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe511-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="fe511-149">範例：`<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="fe511-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="fe511-150">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe511-150">See also</span></span>

- [<span data-ttu-id="fe511-151">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="fe511-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="fe511-152">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="fe511-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="fe511-153">啟用網路追蹤</span><span class="sxs-lookup"><span data-stu-id="fe511-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="fe511-154">追蹤和稽核應用程式</span><span class="sxs-lookup"><span data-stu-id="fe511-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
