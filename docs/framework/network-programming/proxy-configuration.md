---
title: Proxy 組態
ms.date: 06/18/2018
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
ms.openlocfilehash: 30b61a662170b87a557a1a2ea094301ba6401742
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608665"
---
# <a name="proxy-configuration"></a><span data-ttu-id="8b365-102">Proxy 組態</span><span class="sxs-lookup"><span data-stu-id="8b365-102">Proxy Configuration</span></span>
<span data-ttu-id="8b365-103">Proxy 伺服器可處理資源的用戶端要求。</span><span class="sxs-lookup"><span data-stu-id="8b365-103">A proxy server handles client requests for resources.</span></span> <span data-ttu-id="8b365-104">Proxy 可從其快取傳回要求的資源，或將要求轉送至資源所在的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8b365-104">A proxy can return a requested resource from its cache or forward the request to the server where the resource resides.</span></span> <span data-ttu-id="8b365-105">Proxy 可透過減少傳送至遠端伺服器的要求數目，來提升網路效能。</span><span class="sxs-lookup"><span data-stu-id="8b365-105">Proxies can improve network performance by reducing the number of requests sent to remote servers.</span></span> <span data-ttu-id="8b365-106">Proxy 也可用來限制對資源的存取。</span><span class="sxs-lookup"><span data-stu-id="8b365-106">Proxies can also be used to restrict access to resources.</span></span>  
  
## <a name="adaptive-proxies"></a><span data-ttu-id="8b365-107">調適型 Proxy</span><span class="sxs-lookup"><span data-stu-id="8b365-107">Adaptive Proxies</span></span>  
 <span data-ttu-id="8b365-108">.NET Framework 提供兩種 Proxy：調適型和靜態。</span><span class="sxs-lookup"><span data-stu-id="8b365-108">In the .NET Framework, proxies come in two varieties: adaptive and static.</span></span> <span data-ttu-id="8b365-109">調適型 Proxy 會在網路設定變更時調整其設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-109">Adaptive proxies adjust their settings when the network configuration changes.</span></span> <span data-ttu-id="8b365-110">例如，如果膝上型電腦使用者啟動撥接網路連線，調適型 Proxy 會認可這項變更、探索及執行其新的組態指令碼，然後適當地調整其設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-110">For example, if a laptop user starts a dialup network connection, an adaptive proxy would recognize this change, discover and run its new configuration script, and adjust its settings appropriately.</span></span>  
  
 <span data-ttu-id="8b365-111">調適型 Proxy 是由組態指令碼所設定 (請參閱[自動 Proxy 偵測](../../../docs/framework/network-programming/automatic-proxy-detection.md))。</span><span class="sxs-lookup"><span data-stu-id="8b365-111">Adaptive proxies are configured by a configuration script (see [Automatic Proxy Detection](../../../docs/framework/network-programming/automatic-proxy-detection.md)).</span></span> <span data-ttu-id="8b365-112">這個指令碼會產生一組應用程式通訊協定，並為每個通訊協定產生一個 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8b365-112">The script generates a set of application protocols and a proxy for each protocol.</span></span>  
  
 <span data-ttu-id="8b365-113">網路環境的變更可能會要求系統使用一組新的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8b365-113">Changes in the network environment may require that the system use a new set of proxies.</span></span> <span data-ttu-id="8b365-114">如果網路連線中斷或已初始化新的網路連線，系統必須在新環境中找出組態指令碼的適當來源，並執行新的指令碼。</span><span class="sxs-lookup"><span data-stu-id="8b365-114">If a network connection goes down or a new network connection is initialized, the system must discover the appropriate source of the configuration script in the new environment and run the new script.</span></span>  
  
 <span data-ttu-id="8b365-115">您可以在組態檔中使用 [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) 項目的 `usesystemdefault` 屬性。</span><span class="sxs-lookup"><span data-stu-id="8b365-115">You can use the `usesystemdefault` attribute of the [`<proxy>`](../configure-apps/file-schema/network/proxy-element-network-settings.md) element in your configuration file.</span></span> <span data-ttu-id="8b365-116">`usesystemdefault` 屬性控制是否應該從使用者的 Internet Explorer Proxy 設定讀取靜態 Proxy 設定 (Proxy 位址、略過清單和在本機上略過)。</span><span class="sxs-lookup"><span data-stu-id="8b365-116">The `usesystemdefault` attribute controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8b365-117">如果這個值設定為 `true`，則會使用來自 Internet Explorer 的靜態 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-117">If this value is set to `true`, the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8b365-118">如果這個值為 `false` 或未設定，則可以在組態中指定靜態 Proxy 設定，並且這個設定將覆寫 Internet Explorer Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-118">If this value is `false` or not set, the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8b365-119">若要啟用調適型 Proxy，也必須將這個值設定為 `false` 或不設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-119">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>  
  
 <span data-ttu-id="8b365-120">下列範例示範一般調適型 Proxy 組態。</span><span class="sxs-lookup"><span data-stu-id="8b365-120">The following example shows a typical adaptive proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy usesystemdefault="false" />
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a><span data-ttu-id="8b365-121">靜態 Proxy</span><span class="sxs-lookup"><span data-stu-id="8b365-121">Static Proxies</span></span>  
 <span data-ttu-id="8b365-122">靜態 Proxy 通常會由應用程式明確設定，或在應用程式或系統叫用組態檔時明確設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-122">Static proxies are usually configured explicitly by an application, or when a configuration file is invoked by an application or the system.</span></span> <span data-ttu-id="8b365-123">靜態 proxy 可用於拓撲不常變更的網路中，例如連線至公司網路的桌面電腦。</span><span class="sxs-lookup"><span data-stu-id="8b365-123">Static proxies are useful in networks in which the topology changes infrequently, such as a desktop computer connected to a corporate network.</span></span>  
  
 <span data-ttu-id="8b365-124">您有數個選項可控制靜態 Proxy 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="8b365-124">Several options control how a static proxy operates.</span></span> <span data-ttu-id="8b365-125">您可以指定下列各項：</span><span class="sxs-lookup"><span data-stu-id="8b365-125">You can specify the following:</span></span>  
  
-   <span data-ttu-id="8b365-126">Proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="8b365-126">The address of the proxy.</span></span>  
  
-   <span data-ttu-id="8b365-127">是否應該讓本機位址略過 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8b365-127">Whether the proxy should be bypassed for local addresses.</span></span>  
  
-   <span data-ttu-id="8b365-128">是否應該讓一組位址略過 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8b365-128">Whether the proxy should be bypassed for a set of addresses.</span></span>  
  
 <span data-ttu-id="8b365-129">下表顯示靜態 Proxy 的組態選項。</span><span class="sxs-lookup"><span data-stu-id="8b365-129">The following table shows the configuration options for a static proxy.</span></span>  
  
|<span data-ttu-id="8b365-130">屬性 (Attribute)、屬性 (Property) 或組態檔設定</span><span class="sxs-lookup"><span data-stu-id="8b365-130">Attribute, property, or configuration file setting</span></span>|<span data-ttu-id="8b365-131">說明</span><span class="sxs-lookup"><span data-stu-id="8b365-131">Description</span></span>|  
|--------------------------------------------------------|-----------------|  
|<span data-ttu-id="8b365-132">`proxyaddress` 或 <xref:System.Net.WebProxy.Address></span><span class="sxs-lookup"><span data-stu-id="8b365-132">`proxyaddress` or <xref:System.Net.WebProxy.Address></span></span>|<span data-ttu-id="8b365-133">所要使用的 Proxy 位址。</span><span class="sxs-lookup"><span data-stu-id="8b365-133">The address of the proxy to use.</span></span>|  
|<span data-ttu-id="8b365-134">`bypassonlocal` 或 <xref:System.Net.WebProxy.BypassProxyOnLocal></span><span class="sxs-lookup"><span data-stu-id="8b365-134">`bypassonlocal` or <xref:System.Net.WebProxy.BypassProxyOnLocal></span></span>|<span data-ttu-id="8b365-135">控制本機位址是否要略過 Proxy。</span><span class="sxs-lookup"><span data-stu-id="8b365-135">Controls whether the proxy is bypassed for local addresses.</span></span>|  
|<span data-ttu-id="8b365-136">`bypasslist` 或 <xref:System.Net.WebProxy.BypassArrayList></span><span class="sxs-lookup"><span data-stu-id="8b365-136">`bypasslist` or <xref:System.Net.WebProxy.BypassArrayList></span></span>|<span data-ttu-id="8b365-137">使用規則運算式描述一組略過 Proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="8b365-137">Describes, with regular expressions, a set of addresses that bypass the proxy.</span></span>|  
|`usesystemdefault`|<span data-ttu-id="8b365-138">控制是否應該從使用者的 Internet Explorer Proxy 設定讀取靜態 Proxy 設定 (Proxy 位址、略過清單和在本機上略過)。</span><span class="sxs-lookup"><span data-stu-id="8b365-138">Controls whether the static proxy settings (proxy address, bypass list, and bypass on local) should be read from the Internet Explorer proxy settings for the user.</span></span> <span data-ttu-id="8b365-139">如果這個值設定為 `true`，則會使用來自 Internet Explorer 的靜態 Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-139">If this value is set to `true`, then the static proxy settings from Internet Explorer will be used.</span></span> <span data-ttu-id="8b365-140">在 .NET Framework 2.0 上，當這個值設定為 `true` 時，Internet Explorer Proxy 設定不會由組態檔中的其他 Proxy 設定覆寫。</span><span class="sxs-lookup"><span data-stu-id="8b365-140">On .NET Framework 2.0 when this value is set to `true`, the Internet Explorer proxy settings are not overridden by other proxy settings in the configuration file.</span></span> <span data-ttu-id="8b365-141">在 .NET Framework 1.1 上，Internet Explorer Proxy 設定可能會由組態檔中的其他 Proxy 設定覆寫。</span><span class="sxs-lookup"><span data-stu-id="8b365-141">On .NET Framework 1.1, the Internet Explorer proxy settings can be overridden by other proxy settings in the configuration file.</span></span><br /><br /> <span data-ttu-id="8b365-142">如果這個值為 `false` 或未設定，則可以在組態中指定靜態 Proxy 設定；並且這個設定將覆寫 Internet Explorer Proxy 設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-142">If this value is `false` or not set, then the static proxy settings can be specified in the configuration and will override the Internet Explorer proxy settings.</span></span> <span data-ttu-id="8b365-143">若要啟用調適型 Proxy，也必須將這個值設定為 `false` 或不設定。</span><span class="sxs-lookup"><span data-stu-id="8b365-143">This value must also be set to `false` or not set for adaptive proxies to be enabled.</span></span>|  
  
 <span data-ttu-id="8b365-144">下列範例示範一般靜態 Proxy 組態。</span><span class="sxs-lookup"><span data-stu-id="8b365-144">The following example shows a typical static proxy configuration.</span></span>  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8b365-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b365-145">See also</span></span>
- <xref:System.Net.WebProxy>
- <xref:System.Net.GlobalProxySelection>
- [<span data-ttu-id="8b365-146">自動 Proxy 偵測</span><span class="sxs-lookup"><span data-stu-id="8b365-146">Automatic Proxy Detection</span></span>](../../../docs/framework/network-programming/automatic-proxy-detection.md)
