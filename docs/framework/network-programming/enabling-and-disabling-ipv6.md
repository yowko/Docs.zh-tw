---
title: 啟用和停用 IPv6
description: 遵循這些設定步驟來啟用使用 IPv6 通訊協定，包括修改電腦或應用程式的設定檔。
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 00a59e25731d276d81ba74af086b3e19e68d5fad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250537"
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="d5898-103">啟用和停用 IPv6</span><span class="sxs-lookup"><span data-stu-id="d5898-103">Enabling and Disabling IPv6</span></span>

<span data-ttu-id="d5898-104">若要使用 IPv6 通訊協定，請確定您執行的作業系統版本支援 IPv6，並確認已正確設定作業系統和網路類別。</span><span class="sxs-lookup"><span data-stu-id="d5898-104">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="d5898-105">設定步驟</span><span class="sxs-lookup"><span data-stu-id="d5898-105">Configuration Steps</span></span>  

 <span data-ttu-id="d5898-106">下表列出各種組態</span><span class="sxs-lookup"><span data-stu-id="d5898-106">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="d5898-107">作業系統是否啟用 IPv6？</span><span class="sxs-lookup"><span data-stu-id="d5898-107">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="d5898-108">網路類別是否啟用 IPv6？</span><span class="sxs-lookup"><span data-stu-id="d5898-108">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="d5898-109">描述</span><span class="sxs-lookup"><span data-stu-id="d5898-109">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="d5898-110">否</span><span class="sxs-lookup"><span data-stu-id="d5898-110">No</span></span>|<span data-ttu-id="d5898-111">否</span><span class="sxs-lookup"><span data-stu-id="d5898-111">No</span></span>|<span data-ttu-id="d5898-112">可以剖析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-112">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="d5898-113">否</span><span class="sxs-lookup"><span data-stu-id="d5898-113">No</span></span>|<span data-ttu-id="d5898-114">是</span><span class="sxs-lookup"><span data-stu-id="d5898-114">Yes</span></span>|<span data-ttu-id="d5898-115">可以剖析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-115">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="d5898-116">是</span><span class="sxs-lookup"><span data-stu-id="d5898-116">Yes</span></span>|<span data-ttu-id="d5898-117">否</span><span class="sxs-lookup"><span data-stu-id="d5898-117">No</span></span>|<span data-ttu-id="d5898-118">使用未標記為已淘汰的名稱解析方法，可以剖析 IPv6 位址並解析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-118">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="d5898-119">是</span><span class="sxs-lookup"><span data-stu-id="d5898-119">Yes</span></span>|<span data-ttu-id="d5898-120">是</span><span class="sxs-lookup"><span data-stu-id="d5898-120">Yes</span></span>|<span data-ttu-id="d5898-121">使用所有的方法，包括標記為已淘汰的在內，可以剖析和解析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-121">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="d5898-122">請注意，若要在 System.Net 命名空間中啟用所有類別的 IPv6 支援，您必須修改電腦組態檔或應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="d5898-122">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="d5898-123">應用程式組態檔的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="d5898-123">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="d5898-124">如需如何修改電腦組態檔 *machine.config* 的範例，以啟用 Ipv6 支援，請參閱 [如何：修改電腦組態檔以啟用 Ipv6 支援](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。</span><span class="sxs-lookup"><span data-stu-id="d5898-124">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="d5898-125">此外，確定作業系統已啟用 IPv6 支援。</span><span class="sxs-lookup"><span data-stu-id="d5898-125">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="d5898-126">.NET Framework 在組態檔中設定的組態參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5898-126">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>  
  ...  
  <settings>  
    ...  
    <ipv6 enabled="true"/>  
    ...  
  </settings>  
  ...  
</system.net>  
```  
  
 <span data-ttu-id="d5898-127">如果是 .NET Framework 1.1 版及更早版本，[已啟用 IPv6] 組態參數的值會指定 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員是否傳回 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-127">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="d5898-128">針對 .NET Framework 2.0 版及更新版本，如果 Windows 支援 IPv6，則 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員 (例如，<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法) 將會傳回含有一個限制的 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="d5898-128">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="d5898-129">DNS <xref:System.Net.Dns?displayProperty=nameWithType> 已淘汰的成員 (例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法) 會讀取並辨識組態檔中啟用 ipv6 設定的值。</span><span class="sxs-lookup"><span data-stu-id="d5898-129">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5898-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5898-130">See also</span></span>

- [<span data-ttu-id="d5898-131">網際網路通訊協定第 6 版</span><span class="sxs-lookup"><span data-stu-id="d5898-131">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="d5898-132">通訊端</span><span class="sxs-lookup"><span data-stu-id="d5898-132">Sockets</span></span>](sockets.md)
- [<span data-ttu-id="d5898-133">網路設定架構</span><span class="sxs-lookup"><span data-stu-id="d5898-133">Network Settings Schema</span></span>](../configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="d5898-134">\<ipv6> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="d5898-134">\<ipv6> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/ipv6-element-network-settings.md)
