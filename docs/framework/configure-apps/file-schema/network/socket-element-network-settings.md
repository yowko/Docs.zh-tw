---
title: '&lt;通訊端&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
author: mcleblanc
ms.author: markl
ms.openlocfilehash: fb057ab75c31edd7bbdaf5d5115cda2802d3b057
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028254"
---
# <a name="ltsocketgt-element-network-settings"></a><span data-ttu-id="581e9-102">&lt;通訊端&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="581e9-102">&lt;socket&gt; Element (Network Settings)</span></span>
<span data-ttu-id="581e9-103">指定通訊端作業是否使用完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="581e9-103">Specifies whether socket operations use completion ports.</span></span>  
  
 <span data-ttu-id="581e9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="581e9-104">\<configuration></span></span>  
<span data-ttu-id="581e9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="581e9-105">\<system.net></span></span>  
<span data-ttu-id="581e9-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="581e9-106">\<settings></span></span>  
<span data-ttu-id="581e9-107">\<通訊端 ></span><span class="sxs-lookup"><span data-stu-id="581e9-107">\<socket></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="581e9-108">語法</span><span class="sxs-lookup"><span data-stu-id="581e9-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="581e9-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="581e9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="581e9-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="581e9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="581e9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="581e9-111">Attributes</span></span>  
  
|<span data-ttu-id="581e9-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="581e9-112">**Attribute**</span></span>|<span data-ttu-id="581e9-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="581e9-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="581e9-114">表示通訊端是否應該永遠使用完成通訊埠的接受方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="581e9-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="581e9-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="581e9-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="581e9-116">表示通訊端是否應該永遠使用完成通訊埠的連線方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="581e9-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="581e9-117">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="581e9-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="581e9-118">指定的預設<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>用於通訊端。</span><span class="sxs-lookup"><span data-stu-id="581e9-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="581e9-119">預設值取決於 Windows 的版本。</span><span class="sxs-lookup"><span data-stu-id="581e9-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="581e9-120">子元素</span><span class="sxs-lookup"><span data-stu-id="581e9-120">Child Elements</span></span>  
 <span data-ttu-id="581e9-121">無。</span><span class="sxs-lookup"><span data-stu-id="581e9-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="581e9-122">父項目</span><span class="sxs-lookup"><span data-stu-id="581e9-122">Parent Elements</span></span>  
  
|<span data-ttu-id="581e9-123">**目**</span><span class="sxs-lookup"><span data-stu-id="581e9-123">**Element**</span></span>|<span data-ttu-id="581e9-124">**描述**</span><span class="sxs-lookup"><span data-stu-id="581e9-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="581e9-125">設定</span><span class="sxs-lookup"><span data-stu-id="581e9-125">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="581e9-126">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="581e9-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="581e9-127">備註</span><span class="sxs-lookup"><span data-stu-id="581e9-127">Remarks</span></span>  
 <span data-ttu-id="581e9-128">`alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。</span><span class="sxs-lookup"><span data-stu-id="581e9-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="581e9-129">高效能伺服器應用程式的建議完成連接埠。</span><span class="sxs-lookup"><span data-stu-id="581e9-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="581e9-130">預設值`alwaysUseCompletionPortsForAccept`並`alwaysUseCompletionPortsForConnect`屬性是**false**。</span><span class="sxs-lookup"><span data-stu-id="581e9-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="581e9-131"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>可用來取得目前的值`alwaysUseCompletionPortsForAccept`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="581e9-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="581e9-132"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>可用來取得目前的值`alwaysUseCompletionPortsForConnect`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="581e9-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="581e9-133">`ipProtectionLevel`屬性會指定預設<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>用於通訊端。</span><span class="sxs-lookup"><span data-stu-id="581e9-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="581e9-134"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性在例如地址的相同連結本機或網站本機首碼，可讓您設定在指定的範圍，IPv6 通訊端的限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="581e9-135">此選項可讓 IPv6 通訊端上的存取限制的應用程式。</span><span class="sxs-lookup"><span data-stu-id="581e9-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="581e9-136">這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。</span><span class="sxs-lookup"><span data-stu-id="581e9-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="581e9-137">此選項可放大或縮小接聽通訊端，從公用和私用使用者，請在適當時機，或只限相同的站台，視需要存取啟用不受限制的存取範圍。</span><span class="sxs-lookup"><span data-stu-id="581e9-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="581e9-138">這`ipProtectionLevel`屬性設定會影響初始的連入流量：</span><span class="sxs-lookup"><span data-stu-id="581e9-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
-   <span data-ttu-id="581e9-139">TCP 伺服器接聽的通訊端上的連入連線。</span><span class="sxs-lookup"><span data-stu-id="581e9-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
-   <span data-ttu-id="581e9-140">接收通訊端上的封包的 UDP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="581e9-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="581e9-141">此組態設定不會影響已經建立的 TCP 連線 （流量不受限制的兩個方向），而且不會影響應用程式會傳送 UDP 封包。</span><span class="sxs-lookup"><span data-stu-id="581e9-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="581e9-142">可能值`ipProtectionLevel`屬性設定中指定的已定義的保護層級對應至<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>列舉型別，如下所示：</span><span class="sxs-lookup"><span data-stu-id="581e9-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="581e9-143">**屬性值**</span><span class="sxs-lookup"><span data-stu-id="581e9-143">**Attribute Value**</span></span>|<span data-ttu-id="581e9-144">**描述**</span><span class="sxs-lookup"><span data-stu-id="581e9-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="581e9-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="581e9-145">EdgeRestricted</span></span>|<span data-ttu-id="581e9-146">IP 保護層級有臨界限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="581e9-147">若要在網際網路上操作所設計的應用程式會使用此值。</span><span class="sxs-lookup"><span data-stu-id="581e9-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="581e9-148">此設定不允許使用 Windows Teredo 實作的網路位址轉譯 (NAT) 周遊。</span><span class="sxs-lookup"><span data-stu-id="581e9-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="581e9-149">這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式導向的開啟連接埠的網際網路攻擊。</span><span class="sxs-lookup"><span data-stu-id="581e9-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="581e9-150">在 Windows Server 2003 和 Windows XP 上，通訊端 IP 保護層級的預設值有臨界限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="581e9-151">限制</span><span class="sxs-lookup"><span data-stu-id="581e9-151">Restricted</span></span>|<span data-ttu-id="581e9-152">IP 保護層級會受到限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-152">The IP protection level is restricted.</span></span> <span data-ttu-id="581e9-153">未實作網際網路案例的內部網路應用程式會使用此值。</span><span class="sxs-lookup"><span data-stu-id="581e9-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="581e9-154">這些應用程式通常未測試或對抗網際網路型攻擊。</span><span class="sxs-lookup"><span data-stu-id="581e9-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="581e9-155">此設定會限制只有連結-本機接收的流量。</span><span class="sxs-lookup"><span data-stu-id="581e9-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="581e9-156">無限制的</span><span class="sxs-lookup"><span data-stu-id="581e9-156">Unrestricted</span></span>|<span data-ttu-id="581e9-157">IP 保護層級不受限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="581e9-158">這個值會由設計在整個網際網路、 包括利用內建的 IPv6 NAT 周遊功能的應用程式運作的應用程式到 Windows (例如 Teredo)。</span><span class="sxs-lookup"><span data-stu-id="581e9-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="581e9-159">這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式導向的開啟連接埠的網際網路攻擊。</span><span class="sxs-lookup"><span data-stu-id="581e9-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="581e9-160">在 Windows Server 2008 R2 和 Windows Vista 上，通訊端 IP 保護層級的預設值是不受限制的。</span><span class="sxs-lookup"><span data-stu-id="581e9-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="581e9-161">未指定</span><span class="sxs-lookup"><span data-stu-id="581e9-161">Unspecified</span></span>|<span data-ttu-id="581e9-162">未指定 IP 保護層級。</span><span class="sxs-lookup"><span data-stu-id="581e9-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="581e9-163">在 Windows 7 和 Windows Server 2008 R2 上，通訊端 IP 保護層級的預設值是未指定。</span><span class="sxs-lookup"><span data-stu-id="581e9-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="581e9-164">預設值`ipProtectionLevel`屬性是**Unspecified**。</span><span class="sxs-lookup"><span data-stu-id="581e9-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="581e9-165"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可用來取得目前的值`ipProtectionLevel`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="581e9-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="581e9-166">組態檔</span><span class="sxs-lookup"><span data-stu-id="581e9-166">Configuration Files</span></span>  
 <span data-ttu-id="581e9-167">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="581e9-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="581e9-168">範例</span><span class="sxs-lookup"><span data-stu-id="581e9-168">Example</span></span>  
 <span data-ttu-id="581e9-169">下列範例示範如何指定應該使用完成通訊埠，預設值<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>應該是不受限制。</span><span class="sxs-lookup"><span data-stu-id="581e9-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="581e9-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="581e9-170">See Also</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>  
 [<span data-ttu-id="581e9-171">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="581e9-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
