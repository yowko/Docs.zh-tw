---
title: <servicePointManager> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6a40d97bf16a3125452311e7762617e657ca384
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659150"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="6a287-102">\<servicePointManager > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="6a287-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="6a287-103">設定網路資源的連接。</span><span class="sxs-lookup"><span data-stu-id="6a287-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="6a287-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6a287-104">\<configuration></span></span>  
<span data-ttu-id="6a287-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6a287-105">\<system.net></span></span>  
<span data-ttu-id="6a287-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="6a287-106">\<settings></span></span>  
<span data-ttu-id="6a287-107">\<servicePointManager></span><span class="sxs-lookup"><span data-stu-id="6a287-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a287-108">語法</span><span class="sxs-lookup"><span data-stu-id="6a287-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a287-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6a287-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6a287-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6a287-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a287-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6a287-111">Attributes</span></span>  
  
|<span data-ttu-id="6a287-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="6a287-112">**Attribute**</span></span>|<span data-ttu-id="6a287-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="6a287-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="6a287-114">指定系統是否應該先確認憑證上的名稱符合伺服器主機名稱, 然後再使用憑證。</span><span class="sxs-lookup"><span data-stu-id="6a287-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="6a287-115">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6a287-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="6a287-116">指定系統是否應該先檢查憑證是否已被撤銷, 再使用憑證。</span><span class="sxs-lookup"><span data-stu-id="6a287-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="6a287-117">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6a287-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="6a287-118">指定功能變數名稱服務 (DNS) 解析與 DNS 迴圈配置資源選項的快取時間長度 (以毫秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="6a287-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="6a287-119">預設值為 120,000 毫秒 (兩分鐘)。</span><span class="sxs-lookup"><span data-stu-id="6a287-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="6a287-120">指定具有多個網際網路通訊協定 (IP) 位址之主機名稱的 DNS 解析是否會傳回所有位址, 或只傳回第一個位址。</span><span class="sxs-lookup"><span data-stu-id="6a287-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="6a287-121">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6a287-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="6a287-122">指定套用至<xref:System.Net.ServicePointManager>實例上 SSL/TLS 會話的加密原則。</span><span class="sxs-lookup"><span data-stu-id="6a287-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="6a287-123">可能的值相當於<xref:System.Net.Security.EncryptionPolicy>列舉的值。</span><span class="sxs-lookup"><span data-stu-id="6a287-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="6a287-124">當加密原則<xref:System.Security.Authentication.CipherAlgorithmType.Null>設定為`NoEncryption`時, 需要使用。</span><span class="sxs-lookup"><span data-stu-id="6a287-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="6a287-125">預設值為 `RequireEncryption`。</span><span class="sxs-lookup"><span data-stu-id="6a287-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="6a287-126">指定 POST 方法是否預期會收到`100-continue`伺服器的回應。</span><span class="sxs-lookup"><span data-stu-id="6a287-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="6a287-127">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6a287-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="6a287-128">指定服務點管理員所控制的連接是否使用 Nagle 演算法。</span><span class="sxs-lookup"><span data-stu-id="6a287-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="6a287-129">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6a287-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a287-130">子元素</span><span class="sxs-lookup"><span data-stu-id="6a287-130">Child Elements</span></span>  
 <span data-ttu-id="6a287-131">無。</span><span class="sxs-lookup"><span data-stu-id="6a287-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a287-132">父項目</span><span class="sxs-lookup"><span data-stu-id="6a287-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6a287-133">**目**</span><span class="sxs-lookup"><span data-stu-id="6a287-133">**Element**</span></span>|<span data-ttu-id="6a287-134">**描述**</span><span class="sxs-lookup"><span data-stu-id="6a287-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6a287-135">設定</span><span class="sxs-lookup"><span data-stu-id="6a287-135">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="6a287-136">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="6a287-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a287-137">備註</span><span class="sxs-lookup"><span data-stu-id="6a287-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6a287-138">組態檔</span><span class="sxs-lookup"><span data-stu-id="6a287-138">Configuration Files</span></span>  
 <span data-ttu-id="6a287-139">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="6a287-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a287-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a287-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="6a287-141">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6a287-141">Network Settings Schema</span></span>](index.md)
