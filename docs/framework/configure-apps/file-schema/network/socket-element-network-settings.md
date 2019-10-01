---
title: <socket> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: ec2c8388411e24940041dc9dcb7f6a6755e89805
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697579"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="2a712-102">@no__t 0socket > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="2a712-102">\<socket> Element (Network Settings)</span></span>
<span data-ttu-id="2a712-103">指定通訊端作業是否使用完成埠。</span><span class="sxs-lookup"><span data-stu-id="2a712-103">Specifies whether socket operations use completion ports.</span></span>  
  
[<span data-ttu-id="2a712-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2a712-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2a712-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2a712-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="2a712-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2a712-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="2a712-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<socket >**</span><span class="sxs-lookup"><span data-stu-id="2a712-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a712-108">語法</span><span class="sxs-lookup"><span data-stu-id="2a712-108">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a712-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a712-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2a712-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a712-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a712-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2a712-111">Attributes</span></span>  
  
|<span data-ttu-id="2a712-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="2a712-112">**Attribute**</span></span>|<span data-ttu-id="2a712-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="2a712-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="2a712-114">指出通訊端是否應一律使用完成埠來接受方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="2a712-114">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="2a712-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2a712-115">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="2a712-116">指出通訊端是否應一律使用完成埠來進行 Connect 方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="2a712-116">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="2a712-117">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2a712-117">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="2a712-118">指定要用於通訊端的預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2a712-118">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="2a712-119">預設值取決於 Windows 的版本。</span><span class="sxs-lookup"><span data-stu-id="2a712-119">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a712-120">子元素</span><span class="sxs-lookup"><span data-stu-id="2a712-120">Child Elements</span></span>  
 <span data-ttu-id="2a712-121">無。</span><span class="sxs-lookup"><span data-stu-id="2a712-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a712-122">父項目</span><span class="sxs-lookup"><span data-stu-id="2a712-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2a712-123">**目**</span><span class="sxs-lookup"><span data-stu-id="2a712-123">**Element**</span></span>|<span data-ttu-id="2a712-124">**描述**</span><span class="sxs-lookup"><span data-stu-id="2a712-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2a712-125">設置</span><span class="sxs-lookup"><span data-stu-id="2a712-125">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2a712-126">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="2a712-126">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a712-127">備註</span><span class="sxs-lookup"><span data-stu-id="2a712-127">Remarks</span></span>  
 <span data-ttu-id="2a712-128">`alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。</span><span class="sxs-lookup"><span data-stu-id="2a712-128">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="2a712-129">建議將完成埠用於高效能伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a712-129">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="2a712-130">@No__t-0 和 @no__t 1 屬性的預設值為**false**。</span><span class="sxs-lookup"><span data-stu-id="2a712-130">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="2a712-131">@No__t-0 可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="2a712-131">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="2a712-132">@No__t-0 可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="2a712-132">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2a712-133">@No__t-0 屬性會指定要用於通訊端的預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2a712-133">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="2a712-134">@No__t-0 屬性可讓 IPv6 通訊端的限制設定為指定的範圍，例如具有相同連結本機或網站本機首碼的位址。</span><span class="sxs-lookup"><span data-stu-id="2a712-134">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="2a712-135">此選項可讓應用程式在 IPv6 通訊端上放置存取限制。</span><span class="sxs-lookup"><span data-stu-id="2a712-135">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="2a712-136">這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。</span><span class="sxs-lookup"><span data-stu-id="2a712-136">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="2a712-137">此選項會擴大或縮小接聽通訊端的範圍，並在適當時啟用公用和私用使用者的無限制存取，或視需要限制只有相同網站的存取權。</span><span class="sxs-lookup"><span data-stu-id="2a712-137">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="2a712-138">這個 `ipProtectionLevel` 屬性設定只會影響初始傳入流量：</span><span class="sxs-lookup"><span data-stu-id="2a712-138">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="2a712-139">一台 TCP 伺服器，接聽通訊端上的連入連線。</span><span class="sxs-lookup"><span data-stu-id="2a712-139">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="2a712-140">在通訊端上接收封包的 UDP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a712-140">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="2a712-141">此設定不會影響已建立的 TCP 連線（雙向流量不受限制），也不會影響傳送 UDP 封包的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a712-141">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="2a712-142">@No__t-0 屬性設定的可能值會對應至 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 列舉中所指定的已定義保護層級，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2a712-142">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="2a712-143">**屬性值**</span><span class="sxs-lookup"><span data-stu-id="2a712-143">**Attribute Value**</span></span>|<span data-ttu-id="2a712-144">**描述**</span><span class="sxs-lookup"><span data-stu-id="2a712-144">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="2a712-145">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="2a712-145">EdgeRestricted</span></span>|<span data-ttu-id="2a712-146">IP 保護層級為 [edge 限制]。</span><span class="sxs-lookup"><span data-stu-id="2a712-146">The IP protection level is edge restricted.</span></span> <span data-ttu-id="2a712-147">此值適用于設計為跨網際網路運作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2a712-147">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="2a712-148">此設定不允許使用 Windows Teredo 執行來進行網路位址轉譯（NAT）遍歷。</span><span class="sxs-lookup"><span data-stu-id="2a712-148">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="2a712-149">這些應用程式可能會略過 IPv4 防火牆，因此應用程式必須針對在開啟的埠上導向的網際網路攻擊進行強化。</span><span class="sxs-lookup"><span data-stu-id="2a712-149">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="2a712-150">在 Windows Server 2003 和 Windows XP 上，通訊端上 IP 保護層級的預設值是 [edge 限制]。</span><span class="sxs-lookup"><span data-stu-id="2a712-150">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="2a712-151">約束</span><span class="sxs-lookup"><span data-stu-id="2a712-151">Restricted</span></span>|<span data-ttu-id="2a712-152">IP 保護層級受到限制。</span><span class="sxs-lookup"><span data-stu-id="2a712-152">The IP protection level is restricted.</span></span> <span data-ttu-id="2a712-153">不會執行網際網路案例的內部網路應用程式會使用此值。</span><span class="sxs-lookup"><span data-stu-id="2a712-153">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="2a712-154">這些應用程式通常不會針對網際網路風格的攻擊進行測試或強化。</span><span class="sxs-lookup"><span data-stu-id="2a712-154">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="2a712-155">此設定會將接收到的流量限制為僅限連結-本機。</span><span class="sxs-lookup"><span data-stu-id="2a712-155">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="2a712-156">無限制的</span><span class="sxs-lookup"><span data-stu-id="2a712-156">Unrestricted</span></span>|<span data-ttu-id="2a712-157">IP 保護層級不受限制。</span><span class="sxs-lookup"><span data-stu-id="2a712-157">The IP protection level is unrestricted.</span></span> <span data-ttu-id="2a712-158">此值適用于設計為跨網際網路運作的應用程式，包括利用 Windows 內建的 IPv6 NAT 遍歷功能的應用程式（例如 Teredo）。</span><span class="sxs-lookup"><span data-stu-id="2a712-158">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="2a712-159">這些應用程式可能會略過 IPv4 防火牆，因此應用程式必須針對在開啟的埠上導向的網際網路攻擊進行強化。</span><span class="sxs-lookup"><span data-stu-id="2a712-159">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="2a712-160">在 Windows Server 2008 R2 和 Windows Vista 上，通訊端上 IP 保護層級的預設值是 [不受限制]。</span><span class="sxs-lookup"><span data-stu-id="2a712-160">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="2a712-161">未指定</span><span class="sxs-lookup"><span data-stu-id="2a712-161">Unspecified</span></span>|<span data-ttu-id="2a712-162">未指定 IP 保護等級。</span><span class="sxs-lookup"><span data-stu-id="2a712-162">The IP protection level is unspecified.</span></span> <span data-ttu-id="2a712-163">在 Windows 7 和 Windows Server 2008 R2 上，未指定通訊端上 IP 保護層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a712-163">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="2a712-164">**未指定**`ipProtectionLevel` 屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a712-164">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="2a712-165">@No__t-0 屬性可以用來從適用的設定檔中取得 @no__t 1 屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="2a712-165">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2a712-166">組態檔</span><span class="sxs-lookup"><span data-stu-id="2a712-166">Configuration Files</span></span>  
 <span data-ttu-id="2a712-167">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="2a712-167">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a712-168">範例</span><span class="sxs-lookup"><span data-stu-id="2a712-168">Example</span></span>  
 <span data-ttu-id="2a712-169">下列範例示範如何指定應該使用完成埠，以及預設 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 應該不受限制。</span><span class="sxs-lookup"><span data-stu-id="2a712-169">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2a712-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a712-170">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="2a712-171">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2a712-171">Network Settings Schema</span></span>](index.md)
