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
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087462"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="3a54b-102">\<httpWebRequest> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="3a54b-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="3a54b-103">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="3a54b-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="3a54b-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a54b-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a54b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a54b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3a54b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3a54b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a54b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3a54b-107">Attributes</span></span>  
  
|<span data-ttu-id="3a54b-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="3a54b-108">**Attribute**</span></span>|<span data-ttu-id="3a54b-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="3a54b-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="3a54b-110">指定回應標頭的最大長度（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a54b-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="3a54b-111">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="3a54b-111">The default is 64.</span></span> <span data-ttu-id="3a54b-112">-1 值表示回應標頭上不會加諸大小限制。</span><span class="sxs-lookup"><span data-stu-id="3a54b-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="3a54b-113">指定錯誤回應的最大長度（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a54b-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="3a54b-114">預設值為 64。</span><span class="sxs-lookup"><span data-stu-id="3a54b-114">The default is 64.</span></span> <span data-ttu-id="3a54b-115">值為-1 表示不會對錯誤回應施加任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="3a54b-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="3a54b-116">指定上傳以回應未授權錯誤碼的最大長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3a54b-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="3a54b-117">預設值為 -1。</span><span class="sxs-lookup"><span data-stu-id="3a54b-117">The default is -1.</span></span> <span data-ttu-id="3a54b-118">-1 的值表示不會對上載加諸任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="3a54b-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="3a54b-119">指定是否啟用不安全的標頭剖析。</span><span class="sxs-lookup"><span data-stu-id="3a54b-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="3a54b-120">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="3a54b-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a54b-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3a54b-121">Child Elements</span></span>  
 <span data-ttu-id="3a54b-122">無。</span><span class="sxs-lookup"><span data-stu-id="3a54b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a54b-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3a54b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3a54b-124">**元素**</span><span class="sxs-lookup"><span data-stu-id="3a54b-124">**Element**</span></span>|<span data-ttu-id="3a54b-125">**說明**</span><span class="sxs-lookup"><span data-stu-id="3a54b-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3a54b-126">設定</span><span class="sxs-lookup"><span data-stu-id="3a54b-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3a54b-127">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="3a54b-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a54b-128">備註</span><span class="sxs-lookup"><span data-stu-id="3a54b-128">Remarks</span></span>  
 <span data-ttu-id="3a54b-129">根據預設，.NET Framework 會嚴格地強制執行 RFC 2616 以進行 URI 剖析。</span><span class="sxs-lookup"><span data-stu-id="3a54b-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="3a54b-130">某些伺服器回應可能會在禁止的欄位中包含控制字元，而這會導致 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 方法擲回 <xref:System.Net.WebException> 。</span><span class="sxs-lookup"><span data-stu-id="3a54b-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="3a54b-131">如果**useUnsafeHeaderParsing**設定為**true**， <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> 在此情況下將不會擲回; 不過，您的應用程式會很容易受到數種形式的 URI 剖析攻擊。</span><span class="sxs-lookup"><span data-stu-id="3a54b-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="3a54b-132">最佳的解決方法是變更伺服器，讓回應不包含控制字元。</span><span class="sxs-lookup"><span data-stu-id="3a54b-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3a54b-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="3a54b-133">Configuration Files</span></span>  
 <span data-ttu-id="3a54b-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="3a54b-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a54b-135">範例</span><span class="sxs-lookup"><span data-stu-id="3a54b-135">Example</span></span>  
 <span data-ttu-id="3a54b-136">下列範例顯示如何指定大於一般的標頭長度上限。</span><span class="sxs-lookup"><span data-stu-id="3a54b-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a54b-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a54b-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="3a54b-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3a54b-138">Network Settings Schema</span></span>](index.md)
