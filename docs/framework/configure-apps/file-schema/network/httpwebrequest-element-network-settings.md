---
title: "&lt;httpWebRequest&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0a4490870cb12ff221f75b043f01baad9b5c7c96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpwebrequestgt-element-network-settings"></a><span data-ttu-id="5ffbd-102">&lt;httpWebRequest&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="5ffbd-102">&lt;httpWebRequest&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5ffbd-103">可自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="5ffbd-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5ffbd-104">\<configuration></span></span>  
<span data-ttu-id="5ffbd-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="5ffbd-105">\<system.net></span></span>  
<span data-ttu-id="5ffbd-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="5ffbd-106">\<settings></span></span>  
<span data-ttu-id="5ffbd-107">\<httpWebRequest ></span><span class="sxs-lookup"><span data-stu-id="5ffbd-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffbd-108">語法</span><span class="sxs-lookup"><span data-stu-id="5ffbd-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ffbd-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5ffbd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5ffbd-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ffbd-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5ffbd-111">Attributes</span></span>  
  
|<span data-ttu-id="5ffbd-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="5ffbd-112">**Attribute**</span></span>|<span data-ttu-id="5ffbd-113">**說明**</span><span class="sxs-lookup"><span data-stu-id="5ffbd-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="5ffbd-114">指定回應標頭的最大長度，以 kb 為單位。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="5ffbd-115">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-115">The default is 64.</span></span> <span data-ttu-id="5ffbd-116">-1 表示沒有大小限制，將會加諸於回應標頭。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="5ffbd-117">指定錯誤回應，最大的長度，以 kb 為單位。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="5ffbd-118">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-118">The default is 64.</span></span> <span data-ttu-id="5ffbd-119">-1 表示沒有大小限制，將會加諸於錯誤回應。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="5ffbd-120">指定上傳的最大長度，以回應未經授權的錯誤碼，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="5ffbd-121">預設值為 -1。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-121">The default is -1.</span></span> <span data-ttu-id="5ffbd-122">-1 表示沒有大小限制，將會加諸於上傳。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="5ffbd-123">指定是否啟用不安全的標頭解析。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="5ffbd-124">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ffbd-125">子元素</span><span class="sxs-lookup"><span data-stu-id="5ffbd-125">Child Elements</span></span>  
 <span data-ttu-id="5ffbd-126">無。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ffbd-127">父項目</span><span class="sxs-lookup"><span data-stu-id="5ffbd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5ffbd-128">**目**</span><span class="sxs-lookup"><span data-stu-id="5ffbd-128">**Element**</span></span>|<span data-ttu-id="5ffbd-129">**說明**</span><span class="sxs-lookup"><span data-stu-id="5ffbd-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ffbd-130">設定</span><span class="sxs-lookup"><span data-stu-id="5ffbd-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="5ffbd-131">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ffbd-132">備註</span><span class="sxs-lookup"><span data-stu-id="5ffbd-132">Remarks</span></span>  
 <span data-ttu-id="5ffbd-133">根據預設，.NET Framework 嚴格強制 RFC 2616 用於剖析 URI。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="5ffbd-134">某些伺服器的回應可能會禁止在欄位中，這會導致包含控制字元<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>方法會擲回<xref:System.Net.WebException>。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="5ffbd-135">如果**useUnsafeHeaderParsing**設**true**，<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>則不擲回，不過在此情況下，您的應用程式將很容易遭受數種形式的 URI 剖析攻擊。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="5ffbd-136">若要變更伺服器，以便回應不包含控制字元是最佳的解決方案。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5ffbd-137">組態檔</span><span class="sxs-lookup"><span data-stu-id="5ffbd-137">Configuration Files</span></span>  
 <span data-ttu-id="5ffbd-138">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ffbd-139">範例</span><span class="sxs-lookup"><span data-stu-id="5ffbd-139">Example</span></span>  
 <span data-ttu-id="5ffbd-140">下列範例示範如何指定更大的正常最大標頭的長度。</span><span class="sxs-lookup"><span data-stu-id="5ffbd-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ffbd-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ffbd-141">See Also</span></span>  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [<span data-ttu-id="5ffbd-142">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5ffbd-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
