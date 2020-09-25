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
ms.openlocfilehash: b8df32745007b2a145d35b8cfcc4cbd2bd17eb33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201729"
---
# <a name="socket-element-network-settings"></a><span data-ttu-id="910d8-102">\<socket> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="910d8-102">\<socket> Element (Network Settings)</span></span>

<span data-ttu-id="910d8-103">指定通訊端作業是否使用完成埠。</span><span class="sxs-lookup"><span data-stu-id="910d8-103">Specifies whether socket operations use completion ports.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<socket>**

## <a name="syntax"></a><span data-ttu-id="910d8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="910d8-104">Syntax</span></span>  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="910d8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="910d8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="910d8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="910d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="910d8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="910d8-107">Attributes</span></span>  
  
|<span data-ttu-id="910d8-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="910d8-108">**Attribute**</span></span>|<span data-ttu-id="910d8-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="910d8-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|<span data-ttu-id="910d8-110">指出通訊端是否應該一律使用完成接受方法呼叫的埠。</span><span class="sxs-lookup"><span data-stu-id="910d8-110">Indicates whether the socket should always use completion ports for Accept method calls.</span></span> <span data-ttu-id="910d8-111">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="910d8-111">The default value is `false`.</span></span>|  
|`alwaysUseCompletionPortsForConnect`|<span data-ttu-id="910d8-112">指出通訊端是否應該一律使用完成連接方法呼叫的埠。</span><span class="sxs-lookup"><span data-stu-id="910d8-112">Indicates whether the socket should always use completion ports for Connect method calls.</span></span> <span data-ttu-id="910d8-113">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="910d8-113">The default value is `false`.</span></span>|  
|`ipProtectionLevel`|<span data-ttu-id="910d8-114">指定要用於 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 通訊端的預設值。</span><span class="sxs-lookup"><span data-stu-id="910d8-114">Specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="910d8-115">預設值取決於 Windows 版本。</span><span class="sxs-lookup"><span data-stu-id="910d8-115">The default value depends on the version of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="910d8-116">子元素</span><span class="sxs-lookup"><span data-stu-id="910d8-116">Child Elements</span></span>  

 <span data-ttu-id="910d8-117">無。</span><span class="sxs-lookup"><span data-stu-id="910d8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="910d8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="910d8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="910d8-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="910d8-119">**Element**</span></span>|<span data-ttu-id="910d8-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="910d8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="910d8-121">設定</span><span class="sxs-lookup"><span data-stu-id="910d8-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="910d8-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="910d8-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="910d8-123">備註</span><span class="sxs-lookup"><span data-stu-id="910d8-123">Remarks</span></span>  

 <span data-ttu-id="910d8-124">`alwaysUseCompletionPortsForAccept` 和 `alwaysUseCompletionPortsForConnect` 屬性用來指定與 <xref:System.Net.Sockets?displayProperty=nameWithType> 命名空間中的類別使用完成通訊埠有關的預設行為。</span><span class="sxs-lookup"><span data-stu-id="910d8-124">The `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes are used to specify the default behavior regarding the use of completion ports by the classes in the <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace.</span></span> <span data-ttu-id="910d8-125">建議將完成埠用於高效能伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="910d8-125">Completion ports are recommended for high performance server applications.</span></span>  
  
 <span data-ttu-id="910d8-126">和屬性的預設值 `alwaysUseCompletionPortsForAccept` `alwaysUseCompletionPortsForConnect` 為 **false**。</span><span class="sxs-lookup"><span data-stu-id="910d8-126">The default value for the `alwaysUseCompletionPortsForAccept` and `alwaysUseCompletionPortsForConnect` attributes is **false**.</span></span>  
  
 <span data-ttu-id="910d8-127"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>可以用來 `alwaysUseCompletionPortsForAccept` 從適用的設定檔案取得屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="910d8-127">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A> can be used to get the current value of the `alwaysUseCompletionPortsForAccept` attribute from applicable configuration files.</span></span> <span data-ttu-id="910d8-128"><xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>可以用來 `alwaysUseCompletionPortsForConnect` 從適用的設定檔案取得屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="910d8-128">The <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A> can be used to get the current value of the `alwaysUseCompletionPortsForConnect` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="910d8-129">`ipProtectionLevel`屬性會指定要用於 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 通訊端的預設值。</span><span class="sxs-lookup"><span data-stu-id="910d8-129">The `ipProtectionLevel` attribute specifies the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> to use for a socket.</span></span> <span data-ttu-id="910d8-130"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可將 IPv6 通訊端的限制設定為指定的範圍，例如具有相同連結本機或網站本機前置詞的位址。</span><span class="sxs-lookup"><span data-stu-id="910d8-130">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property enables configuration of a restriction for an IPv6 socket to a specified scope, such as addresses with the same link local or site local prefix.</span></span> <span data-ttu-id="910d8-131">此選項可讓應用程式在 IPv6 通訊端上放置存取限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-131">This option enables applications to place access restrictions on IPv6 sockets.</span></span> <span data-ttu-id="910d8-132">這類限制可以讓應用程式在私人 LAN 上執行，簡便又穩當地強化應用程式對外部攻擊的抵禦。</span><span class="sxs-lookup"><span data-stu-id="910d8-132">Such restrictions enable an application running on a private LAN to simply and robustly harden itself against external attacks.</span></span> <span data-ttu-id="910d8-133">此選項可擴大或縮小接聽通訊端的範圍，並在適當時啟用從公用和私用使用者進行無限制的存取，或僅視需要限制存取相同的網站。</span><span class="sxs-lookup"><span data-stu-id="910d8-133">This option widens or narrows the scope of a listening socket, enabling unrestricted access from public and private users when appropriate, or restricting access only to the same site, as required.</span></span>  
  
 <span data-ttu-id="910d8-134">此 `ipProtectionLevel` 屬性設定只會影響初始連入流量：</span><span class="sxs-lookup"><span data-stu-id="910d8-134">This `ipProtectionLevel` attribute setting affects only initial incoming traffic:</span></span>  
  
- <span data-ttu-id="910d8-135">TCP 伺服器，接聽通訊端上的連入連線。</span><span class="sxs-lookup"><span data-stu-id="910d8-135">A TCP server listening for incoming connections on a socket.</span></span>  
  
- <span data-ttu-id="910d8-136">在通訊端上接收封包的 UDP 應用程式。</span><span class="sxs-lookup"><span data-stu-id="910d8-136">A UDP application receiving a packet on a socket.</span></span>  
  
 <span data-ttu-id="910d8-137">這項設定不會影響已建立的 TCP 連線， (流量在雙向未受限制的情況下) ，而且不會影響傳送 UDP 封包的應用程式。</span><span class="sxs-lookup"><span data-stu-id="910d8-137">This configuration setting does not affect already established TCP connections (traffic is unrestricted in both directions) and does not affect an application sending UDP packets.</span></span>  
  
 <span data-ttu-id="910d8-138">屬性設定的可能值會 `ipProtectionLevel` 對應至列舉中所指定的已定義保護層級，如下所示 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="910d8-138">The possible values for the `ipProtectionLevel` attribute setting correspond with the defined protection levels specified in the <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> enumeration as follows:</span></span>  
  
|<span data-ttu-id="910d8-139">**屬性值**</span><span class="sxs-lookup"><span data-stu-id="910d8-139">**Attribute Value**</span></span>|<span data-ttu-id="910d8-140">**說明**</span><span class="sxs-lookup"><span data-stu-id="910d8-140">**Description**</span></span>|  
|-|-|  
|<span data-ttu-id="910d8-141">EdgeRestricted</span><span class="sxs-lookup"><span data-stu-id="910d8-141">EdgeRestricted</span></span>|<span data-ttu-id="910d8-142">IP 保護層級有臨界限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-142">The IP protection level is edge restricted.</span></span> <span data-ttu-id="910d8-143">這個值將由設計在整個網際網路上操作的應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="910d8-143">This value would be used by applications designed to operate across the Internet.</span></span> <span data-ttu-id="910d8-144">此項設定不允許使用 Windows Teredo 實作來進行網路位址轉譯 (NAT) 周遊。</span><span class="sxs-lookup"><span data-stu-id="910d8-144">This setting does not allow Network Address Translation (NAT) traversal using the Windows Teredo implementation.</span></span> <span data-ttu-id="910d8-145">這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。</span><span class="sxs-lookup"><span data-stu-id="910d8-145">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="910d8-146">在 Windows Server 2003 和 Windows XP 環境下，通訊端 IP 保護層級的預設值有臨界限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-146">On Windows Server 2003 and Windows XP, the default value for the IP Protection level on a socket is edge restricted.</span></span>|  
|<span data-ttu-id="910d8-147">Restricted</span><span class="sxs-lookup"><span data-stu-id="910d8-147">Restricted</span></span>|<span data-ttu-id="910d8-148">IP 保護層級有限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-148">The IP protection level is restricted.</span></span> <span data-ttu-id="910d8-149">這個值將由未實作網際網路案例的內部網路應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="910d8-149">This value would be used by intranet applications that do not implement Internet scenarios.</span></span> <span data-ttu-id="910d8-150">這些應用程式通常不會就網路攻擊測試進行測試或是採取強化。</span><span class="sxs-lookup"><span data-stu-id="910d8-150">These applications are generally not tested or hardened against Internet-style attacks.</span></span> <span data-ttu-id="910d8-151">這個設定會將接收傳輸限制於僅連結和本機之間。</span><span class="sxs-lookup"><span data-stu-id="910d8-151">This setting will limit the received traffic to link-local only.</span></span>|  
|<span data-ttu-id="910d8-152">不受限制</span><span class="sxs-lookup"><span data-stu-id="910d8-152">Unrestricted</span></span>|<span data-ttu-id="910d8-153">IP 保護層級不受限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-153">The IP protection level is unrestricted.</span></span> <span data-ttu-id="910d8-154">這個值將由設計在整個網際網路上操作的應用程式使用，包括發揮已內建在 Windows 之 IPv6 NAT 周遊功能的應用程式 (例如 Teredo)。</span><span class="sxs-lookup"><span data-stu-id="910d8-154">This value would be used by applications designed to operate across the Internet, including applications taking advantage of IPv6 NAT traversal capabilities built into Windows (Teredo, for example).</span></span> <span data-ttu-id="910d8-155">這些應用程式可能會略過 IPv4 防火牆，因此必須加強應用程式，以抵禦在開啟的通訊埠位置遭受的直接網路攻擊。</span><span class="sxs-lookup"><span data-stu-id="910d8-155">These applications may bypass IPv4 firewalls, so applications must be hardened against Internet attacks directed at the opened port.</span></span> <span data-ttu-id="910d8-156">在 Windows Server 2008 R2 和 Windows Vista 環境下，通訊端 IP 保護層級的預設值不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-156">On Windows Server 2008 R2 and Windows Vista, the default value for the IP Protection level on a socket is unrestricted.</span></span>|  
|<span data-ttu-id="910d8-157">[未指定]</span><span class="sxs-lookup"><span data-stu-id="910d8-157">Unspecified</span></span>|<span data-ttu-id="910d8-158">IP 保護層級尚未指定。</span><span class="sxs-lookup"><span data-stu-id="910d8-158">The IP protection level is unspecified.</span></span> <span data-ttu-id="910d8-159">在 Windows 7 和 Windows Server 2008 R2 環境下，通訊端 IP 保護層級的預設值尚未指定。</span><span class="sxs-lookup"><span data-stu-id="910d8-159">On Windows 7 and Windows Server 2008 R2, the default value for the IP Protection level on a socket is unspecified.</span></span>|  
  
 <span data-ttu-id="910d8-160">未指定屬性的預設值 `ipProtectionLevel` 。 **Unspecified**</span><span class="sxs-lookup"><span data-stu-id="910d8-160">The default value for the `ipProtectionLevel` attribute is **Unspecified**.</span></span>  
  
 <span data-ttu-id="910d8-161"><xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>屬性可以用來從適用的設定檔案取得屬性的目前值 `ipProtectionLevel` 。</span><span class="sxs-lookup"><span data-stu-id="910d8-161">The <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A> property can be used to get the current value of the `ipProtectionLevel` attribute from applicable configuration files.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="910d8-162">組態檔</span><span class="sxs-lookup"><span data-stu-id="910d8-162">Configuration Files</span></span>  

 <span data-ttu-id="910d8-163">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="910d8-163">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="910d8-164">範例</span><span class="sxs-lookup"><span data-stu-id="910d8-164">Example</span></span>  

 <span data-ttu-id="910d8-165">下列範例示範如何指定應使用完成埠，而且預設值 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> 應該不受限制。</span><span class="sxs-lookup"><span data-stu-id="910d8-165">The following example shows how to specify that completion ports should be used and that the default <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType> should be unrestricted.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="910d8-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="910d8-166">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [<span data-ttu-id="910d8-167">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="910d8-167">Network Settings Schema</span></span>](index.md)
