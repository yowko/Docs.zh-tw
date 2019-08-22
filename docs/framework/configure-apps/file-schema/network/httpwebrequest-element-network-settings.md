---
title: <httpWebRequest> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: de5672e5c6762b1e0742e717a3d499a4f93ee8ec
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659334"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="aed60-102">\<HTTPWebRequest > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="aed60-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="aed60-103">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="aed60-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="aed60-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aed60-104">\<configuration></span></span>  
<span data-ttu-id="aed60-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="aed60-105">\<system.net></span></span>  
<span data-ttu-id="aed60-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="aed60-106">\<settings></span></span>  
<span data-ttu-id="aed60-107">\<httpWebRequest></span><span class="sxs-lookup"><span data-stu-id="aed60-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aed60-108">語法</span><span class="sxs-lookup"><span data-stu-id="aed60-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aed60-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aed60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aed60-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aed60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aed60-111">屬性</span><span class="sxs-lookup"><span data-stu-id="aed60-111">Attributes</span></span>  
  
|<span data-ttu-id="aed60-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="aed60-112">**Attribute**</span></span>|<span data-ttu-id="aed60-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="aed60-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="aed60-114">指定回應標頭的最大長度 (以 kb 為單位)。</span><span class="sxs-lookup"><span data-stu-id="aed60-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="aed60-115">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="aed60-115">The default is 64.</span></span> <span data-ttu-id="aed60-116">-1 值表示回應標頭上不會加諸大小限制。</span><span class="sxs-lookup"><span data-stu-id="aed60-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="aed60-117">指定錯誤回應的最大長度 (以 kb 為單位)。</span><span class="sxs-lookup"><span data-stu-id="aed60-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="aed60-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="aed60-118">The default is 64.</span></span> <span data-ttu-id="aed60-119">值為-1 表示不會對錯誤回應施加任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="aed60-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="aed60-120">指定上傳以回應未授權錯誤碼的最大長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="aed60-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="aed60-121">預設值為 -1。</span><span class="sxs-lookup"><span data-stu-id="aed60-121">The default is -1.</span></span> <span data-ttu-id="aed60-122">-1 值表示上傳時不會加諸大小限制。</span><span class="sxs-lookup"><span data-stu-id="aed60-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="aed60-123">指定是否啟用不安全的標頭剖析。</span><span class="sxs-lookup"><span data-stu-id="aed60-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="aed60-124">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="aed60-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aed60-125">子元素</span><span class="sxs-lookup"><span data-stu-id="aed60-125">Child Elements</span></span>  
 <span data-ttu-id="aed60-126">無。</span><span class="sxs-lookup"><span data-stu-id="aed60-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aed60-127">父項目</span><span class="sxs-lookup"><span data-stu-id="aed60-127">Parent Elements</span></span>  
  
|<span data-ttu-id="aed60-128">**目**</span><span class="sxs-lookup"><span data-stu-id="aed60-128">**Element**</span></span>|<span data-ttu-id="aed60-129">**描述**</span><span class="sxs-lookup"><span data-stu-id="aed60-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="aed60-130">設置</span><span class="sxs-lookup"><span data-stu-id="aed60-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="aed60-131">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="aed60-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aed60-132">備註</span><span class="sxs-lookup"><span data-stu-id="aed60-132">Remarks</span></span>  
 <span data-ttu-id="aed60-133">根據預設, .NET Framework 會嚴格地強制執行 RFC 2616 以進行 URI 剖析。</span><span class="sxs-lookup"><span data-stu-id="aed60-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="aed60-134">某些伺服器回應可能會在禁止的欄位中包含控制字元, 而<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>這會導致方法<xref:System.Net.WebException>擲回。</span><span class="sxs-lookup"><span data-stu-id="aed60-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="aed60-135">如果**useUnsafeHeaderParsing**設定為**true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>在此情況下將不會擲回; 不過, 您的應用程式會很容易受到數種形式的 URI 剖析攻擊。</span><span class="sxs-lookup"><span data-stu-id="aed60-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="aed60-136">最佳的解決方法是變更伺服器, 讓回應不包含控制字元。</span><span class="sxs-lookup"><span data-stu-id="aed60-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="aed60-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="aed60-137">Configuration Files</span></span>  
 <span data-ttu-id="aed60-138">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="aed60-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aed60-139">範例</span><span class="sxs-lookup"><span data-stu-id="aed60-139">Example</span></span>  
 <span data-ttu-id="aed60-140">下列範例顯示如何指定大於一般的標頭長度上限。</span><span class="sxs-lookup"><span data-stu-id="aed60-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aed60-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aed60-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="aed60-142">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="aed60-142">Network Settings Schema</span></span>](index.md)
