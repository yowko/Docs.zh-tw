---
title: <servicePointManager> 項目 (網路設定)
description: <servicePointManager>Network settings 元素會設定 .NET Framework 中網路資源的連線選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504520"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="5bbe8-103">\<servicePointManager> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="5bbe8-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="5bbe8-104">設定網路資源的連接。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="5bbe8-105">語法</span><span class="sxs-lookup"><span data-stu-id="5bbe8-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bbe8-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5bbe8-106">Attributes and Elements</span></span>  
 <span data-ttu-id="5bbe8-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bbe8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5bbe8-108">Attributes</span></span>  
  
|<span data-ttu-id="5bbe8-109">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5bbe8-109">**Attribute**</span></span>|<span data-ttu-id="5bbe8-110">**描述**</span><span class="sxs-lookup"><span data-stu-id="5bbe8-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="5bbe8-111">指定系統是否應該先確認憑證上的名稱符合伺服器主機名稱，然後再使用憑證。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="5bbe8-112">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="5bbe8-113">指定系統是否應該先檢查憑證是否已被撤銷，再使用憑證。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="5bbe8-114">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="5bbe8-115">指定功能變數名稱服務（DNS）解析與 DNS 迴圈配置資源選項的快取時間長度（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="5bbe8-116">預設值為 120,000 毫秒 (兩分鐘)。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="5bbe8-117">指定具有多個網際網路通訊協定（IP）位址之主機名稱的 DNS 解析是否會傳回所有位址，或只傳回第一個位址。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="5bbe8-118">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="5bbe8-119">指定套用至實例上 SSL/TLS 會話的加密原則 <xref:System.Net.ServicePointManager> 。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="5bbe8-120">可能的值相當於列舉的值 <xref:System.Net.Security.EncryptionPolicy> 。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="5bbe8-121"><xref:System.Security.Authentication.CipherAlgorithmType.Null>當加密原則設定為時，需要使用 `NoEncryption` 。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="5bbe8-122">預設值為 `RequireEncryption`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="5bbe8-123">指定 POST 方法是否預期會收到伺服器的 `100-continue` 回應。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="5bbe8-124">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="5bbe8-125">指定服務點管理員所控制的連接是否使用 Nagle 演算法。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="5bbe8-126">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bbe8-127">子元素</span><span class="sxs-lookup"><span data-stu-id="5bbe8-127">Child Elements</span></span>  
 <span data-ttu-id="5bbe8-128">無。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bbe8-129">父項目</span><span class="sxs-lookup"><span data-stu-id="5bbe8-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5bbe8-130">**元素**</span><span class="sxs-lookup"><span data-stu-id="5bbe8-130">**Element**</span></span>|<span data-ttu-id="5bbe8-131">**描述**</span><span class="sxs-lookup"><span data-stu-id="5bbe8-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5bbe8-132">設定</span><span class="sxs-lookup"><span data-stu-id="5bbe8-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="5bbe8-133">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bbe8-134">備註</span><span class="sxs-lookup"><span data-stu-id="5bbe8-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5bbe8-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="5bbe8-135">Configuration Files</span></span>  
 <span data-ttu-id="5bbe8-136">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="5bbe8-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbe8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bbe8-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="5bbe8-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5bbe8-138">Network Settings Schema</span></span>](index.md)
