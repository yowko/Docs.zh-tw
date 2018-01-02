---
title: "&lt;servicePointManager&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 38ffe6728ca05022caca8f5973b546f2b17412d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicepointmanagergt-element-network-settings"></a><span data-ttu-id="de3e1-102">&lt;servicePointManager&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="de3e1-102">&lt;servicePointManager&gt; Element (Network Settings)</span></span>
<span data-ttu-id="de3e1-103">設定連線到網路資源。</span><span class="sxs-lookup"><span data-stu-id="de3e1-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="de3e1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="de3e1-104">\<configuration></span></span>  
<span data-ttu-id="de3e1-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="de3e1-105">\<system.net></span></span>  
<span data-ttu-id="de3e1-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="de3e1-106">\<settings></span></span>  
<span data-ttu-id="de3e1-107">\<servicePointManager ></span><span class="sxs-lookup"><span data-stu-id="de3e1-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de3e1-108">語法</span><span class="sxs-lookup"><span data-stu-id="de3e1-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de3e1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="de3e1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="de3e1-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="de3e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de3e1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="de3e1-111">Attributes</span></span>  
  
|<span data-ttu-id="de3e1-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="de3e1-112">**Attribute**</span></span>|<span data-ttu-id="de3e1-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="de3e1-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="de3e1-114">指定系統是否應該驗證憑證的名稱符合伺服器主機名稱，然後再使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="de3e1-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="de3e1-115">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="de3e1-116">指定系統是否應該檢查是否已撤銷的憑證之前使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="de3e1-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="de3e1-117">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="de3e1-118">指定多久網域名稱服務 (DNS) 解決方案會快取搭配 DNS 循環配置資源 選項，以毫秒為單位。</span><span class="sxs-lookup"><span data-stu-id="de3e1-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="de3e1-119">預設值為 120,000 毫秒 (兩分鐘)。</span><span class="sxs-lookup"><span data-stu-id="de3e1-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="de3e1-120">指定的位址或第一個是否主機的 DNS 解析名稱具有多個傳回的網際網路通訊協定 (IP) 位址。</span><span class="sxs-lookup"><span data-stu-id="de3e1-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="de3e1-121">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="de3e1-122">指定套用到 SSL/TLS 工作階段上的加密原則<xref:System.Net.ServicePointManager>執行個體。</span><span class="sxs-lookup"><span data-stu-id="de3e1-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="de3e1-123">可能的值為相等的值<xref:System.Net.Security.EncryptionPolicy>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="de3e1-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="de3e1-124">使用<xref:System.Security.Authentication.CipherAlgorithmType.Null>時需要加密原則設為`NoEncryption`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="de3e1-125">預設值是 `RequireEncryption`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="de3e1-126">指定是否 POST 方法應該預期會收到`100-continue`來自伺服器的回應。</span><span class="sxs-lookup"><span data-stu-id="de3e1-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="de3e1-127">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="de3e1-128">指定由服務點管理員所控制的連接是否使用 Nagle 演算法。</span><span class="sxs-lookup"><span data-stu-id="de3e1-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="de3e1-129">預設值是 `true`。</span><span class="sxs-lookup"><span data-stu-id="de3e1-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de3e1-130">子元素</span><span class="sxs-lookup"><span data-stu-id="de3e1-130">Child Elements</span></span>  
 <span data-ttu-id="de3e1-131">無。</span><span class="sxs-lookup"><span data-stu-id="de3e1-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de3e1-132">父項目</span><span class="sxs-lookup"><span data-stu-id="de3e1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="de3e1-133">**目**</span><span class="sxs-lookup"><span data-stu-id="de3e1-133">**Element**</span></span>|<span data-ttu-id="de3e1-134">**描述**</span><span class="sxs-lookup"><span data-stu-id="de3e1-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="de3e1-135">設定</span><span class="sxs-lookup"><span data-stu-id="de3e1-135">Settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="de3e1-136">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="de3e1-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de3e1-137">備註</span><span class="sxs-lookup"><span data-stu-id="de3e1-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="de3e1-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="de3e1-138">Configuration Files</span></span>  
 <span data-ttu-id="de3e1-139">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="de3e1-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3e1-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="de3e1-140">See Also</span></span>  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [<span data-ttu-id="de3e1-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="de3e1-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
