---
title: <httpWebRequest> 項目 (網路設定)
description: <httpWebRequest>網路設定元素會自訂 .NET Framework 中的 Web 要求參數。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 86960a33d0924013e2bfbfa743eab372181033b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195424"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="162b4-103">\<httpWebRequest> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="162b4-103">\<httpWebRequest> Element (Network Settings)</span></span>

<span data-ttu-id="162b4-104">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="162b4-104">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="162b4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="162b4-105">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="162b4-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="162b4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="162b4-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="162b4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="162b4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="162b4-108">Attributes</span></span>  
  
|<span data-ttu-id="162b4-109">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="162b4-109">**Attribute**</span></span>|<span data-ttu-id="162b4-110">**說明**</span><span class="sxs-lookup"><span data-stu-id="162b4-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="162b4-111">指定回應標頭的最大長度（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="162b4-111">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="162b4-112">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="162b4-112">The default is 64.</span></span> <span data-ttu-id="162b4-113">-1 的值表示回應標頭上不會加諸任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="162b4-113">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="162b4-114">指定錯誤回應的最大長度（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="162b4-114">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="162b4-115">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="162b4-115">The default is 64.</span></span> <span data-ttu-id="162b4-116">值為-1 表示錯誤回應不會加諸任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="162b4-116">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="162b4-117">指定上傳用來回應未授權錯誤碼的最大長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="162b4-117">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="162b4-118">預設值為 -1。</span><span class="sxs-lookup"><span data-stu-id="162b4-118">The default is -1.</span></span> <span data-ttu-id="162b4-119">-1 的值表示不會對上載加諸任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="162b4-119">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="162b4-120">指定是否啟用 unsafe 標頭剖析。</span><span class="sxs-lookup"><span data-stu-id="162b4-120">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="162b4-121">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="162b4-121">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="162b4-122">子元素</span><span class="sxs-lookup"><span data-stu-id="162b4-122">Child Elements</span></span>  

 <span data-ttu-id="162b4-123">無。</span><span class="sxs-lookup"><span data-stu-id="162b4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="162b4-124">父項目</span><span class="sxs-lookup"><span data-stu-id="162b4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="162b4-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="162b4-125">**Element**</span></span>|<span data-ttu-id="162b4-126">**說明**</span><span class="sxs-lookup"><span data-stu-id="162b4-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="162b4-127">設定</span><span class="sxs-lookup"><span data-stu-id="162b4-127">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="162b4-128">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="162b4-128">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="162b4-129">備註</span><span class="sxs-lookup"><span data-stu-id="162b4-129">Remarks</span></span>  

 <span data-ttu-id="162b4-130">根據預設，.NET Framework 會嚴格地強制執行 RFC 2616 進行 URI 剖析。</span><span class="sxs-lookup"><span data-stu-id="162b4-130">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="162b4-131">某些伺服器回應可能會在禁止的欄位中包含控制字元，這會導致 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 方法擲回 <xref:System.Net.WebException> 。</span><span class="sxs-lookup"><span data-stu-id="162b4-131">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="162b4-132">如果 **useUnsafeHeaderParsing** 設定為 **true**， <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 將不會在此情況下擲回; 不過，您的應用程式將容易遭受數種形式的 URI 剖析攻擊。</span><span class="sxs-lookup"><span data-stu-id="162b4-132">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="162b4-133">最好的解決方法是變更伺服器，讓回應不包含控制字元。</span><span class="sxs-lookup"><span data-stu-id="162b4-133">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="162b4-134">組態檔</span><span class="sxs-lookup"><span data-stu-id="162b4-134">Configuration Files</span></span>  

 <span data-ttu-id="162b4-135">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="162b4-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="162b4-136">範例</span><span class="sxs-lookup"><span data-stu-id="162b4-136">Example</span></span>  

 <span data-ttu-id="162b4-137">下列範例示範如何指定大於標準的最大標頭長度。</span><span class="sxs-lookup"><span data-stu-id="162b4-137">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="162b4-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="162b4-138">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="162b4-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="162b4-139">Network Settings Schema</span></span>](index.md)
