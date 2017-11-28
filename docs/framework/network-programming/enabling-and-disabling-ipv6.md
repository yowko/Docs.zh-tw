---
title: "啟用和停用 IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9edb87cf1ee35ac6848a478552cf8d0732177a81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-and-disabling-ipv6"></a><span data-ttu-id="2d232-102">啟用和停用 IPv6</span><span class="sxs-lookup"><span data-stu-id="2d232-102">Enabling and Disabling IPv6</span></span>
<span data-ttu-id="2d232-103">若要使用 IPv6 通訊協定，請確定您執行的作業系統版本支援 IPv6，並確認已正確設定作業系統和網路類別。</span><span class="sxs-lookup"><span data-stu-id="2d232-103">To use the IPv6 protocol, ensure that you are running a version of the operating system that supports IPv6 and ensure that the operating system and the networking classes are configured properly.</span></span>  
  
## <a name="configuration-steps"></a><span data-ttu-id="2d232-104">設定步驟</span><span class="sxs-lookup"><span data-stu-id="2d232-104">Configuration Steps</span></span>  
 <span data-ttu-id="2d232-105">下表列出各種組態</span><span class="sxs-lookup"><span data-stu-id="2d232-105">The following table lists various configurations</span></span>  
  
|<span data-ttu-id="2d232-106">作業系統是否啟用 IPv6？</span><span class="sxs-lookup"><span data-stu-id="2d232-106">Operating system IPv6-enabled?</span></span>|<span data-ttu-id="2d232-107">網路類別是否啟用 IPv6？</span><span class="sxs-lookup"><span data-stu-id="2d232-107">Networking classes IPv6-enabled?</span></span>|<span data-ttu-id="2d232-108">描述</span><span class="sxs-lookup"><span data-stu-id="2d232-108">Description</span></span>|  
|-------------------------------------|---------------------------------------|-----------------|  
|<span data-ttu-id="2d232-109">否</span><span class="sxs-lookup"><span data-stu-id="2d232-109">No</span></span>|<span data-ttu-id="2d232-110">否</span><span class="sxs-lookup"><span data-stu-id="2d232-110">No</span></span>|<span data-ttu-id="2d232-111">可以剖析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-111">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="2d232-112">否</span><span class="sxs-lookup"><span data-stu-id="2d232-112">No</span></span>|<span data-ttu-id="2d232-113">是</span><span class="sxs-lookup"><span data-stu-id="2d232-113">Yes</span></span>|<span data-ttu-id="2d232-114">可以剖析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-114">Can parse IPv6 addresses.</span></span>|  
|<span data-ttu-id="2d232-115">是</span><span class="sxs-lookup"><span data-stu-id="2d232-115">Yes</span></span>|<span data-ttu-id="2d232-116">否</span><span class="sxs-lookup"><span data-stu-id="2d232-116">No</span></span>|<span data-ttu-id="2d232-117">使用未標記為已淘汰的名稱解析方法，可以剖析 IPv6 位址並解析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-117">Can parse IPv6 addresses and resolve IPv6 addresses using name resolution methods not marked obsolete.</span></span>|  
|<span data-ttu-id="2d232-118">是</span><span class="sxs-lookup"><span data-stu-id="2d232-118">Yes</span></span>|<span data-ttu-id="2d232-119">是</span><span class="sxs-lookup"><span data-stu-id="2d232-119">Yes</span></span>|<span data-ttu-id="2d232-120">使用所有的方法，包括標記為已淘汰的在內，可以剖析和解析 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-120">Can parse and resolve IPv6 addresses using all methods including those marked obsolete.</span></span>|  
  
 <span data-ttu-id="2d232-121">請注意，若要在 System.Net 命名空間中啟用所有類別的 IPv6 支援，您必須修改電腦組態檔或應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="2d232-121">Be aware that to enable the IPv6 support for all classes in the System.Net namespace, you must modify the computer configuration file or the configuration file for the application.</span></span> <span data-ttu-id="2d232-122">應用程式組態檔的優先順序高於電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="2d232-122">The configuration file for an application has precedence over the computer configuration file.</span></span>  
  
 <span data-ttu-id="2d232-123">如需如何修改電腦組態檔 *machine.config* 的範例，以啟用 Ipv6 支援，請參閱[如何：修改電腦組態檔以啟用 Ipv6 支援](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。</span><span class="sxs-lookup"><span data-stu-id="2d232-123">For an example of how to modify the computer configuration file, *machine.config*, to enable Ipv6 support see, [How to: Modify the Computer Configuration File to Enable Ipv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span> <span data-ttu-id="2d232-124">此外，確定作業系統已啟用 IPv6 支援。</span><span class="sxs-lookup"><span data-stu-id="2d232-124">Also, ensure that the IPv6 support is enabled for the operating system.</span></span>  
  
 <span data-ttu-id="2d232-125">.NET Framework 在組態檔中設定的組態參數，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2d232-125">The .NET Framework has a configuration switch set in a configuration file as follows</span></span>  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 <span data-ttu-id="2d232-126">如果是 .NET Framework 1.1 版及更早版本，[已啟用 IPv6] 組態參數的值會指定 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員是否傳回 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-126">For .NET Framework version 1.1 and earlier, the value of the **ipv6 enabled** configuration switch specifies whether members of the <xref:System.Net.Dns?displayProperty=nameWithType> class return IPv6 addresses.</span></span>  
  
 <span data-ttu-id="2d232-127">針對 .NET Framework 2.0 版及更新版本，如果 Windows 支援 IPv6，則 <xref:System.Net.Dns?displayProperty=nameWithType> 類別的成員 (例如，<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法) 將會傳回含有一個限制的 IPv6 位址。</span><span class="sxs-lookup"><span data-stu-id="2d232-127">For .NET Framework version 2.0 and later, if Windows supports IPv6, then members of the <xref:System.Net.Dns?displayProperty=nameWithType> class, (for example, the <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> method), will return IPv6 addresses with one limitation.</span></span> <span data-ttu-id="2d232-128">DNS <xref:System.Net.Dns?displayProperty=nameWithType> 已淘汰的成員 (例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法) 會讀取並辨識組態檔中啟用 ipv6 設定的值。</span><span class="sxs-lookup"><span data-stu-id="2d232-128">Obsolete members of the DNS <xref:System.Net.Dns?displayProperty=nameWithType> (for example, the <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> method) will read and recognize the value in the configuration file for the ipv6 enabled setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d232-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d232-129">See Also</span></span>  
 [<span data-ttu-id="2d232-130">網際網路通訊協定第 6 版</span><span class="sxs-lookup"><span data-stu-id="2d232-130">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [<span data-ttu-id="2d232-131">通訊端</span><span class="sxs-lookup"><span data-stu-id="2d232-131">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)  
 [<span data-ttu-id="2d232-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2d232-132">Network Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="2d232-133">\<ipv6> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="2d232-133">\<ipv6> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
