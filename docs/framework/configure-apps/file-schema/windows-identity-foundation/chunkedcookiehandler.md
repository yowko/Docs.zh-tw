---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252112"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="7c01d-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="7c01d-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="7c01d-102"><xref:System.IdentityModel.Services.ChunkedCookieHandler>設定。</span><span class="sxs-lookup"><span data-stu-id="7c01d-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="7c01d-103">只有當`mode` `<cookieHandler>`元素的屬性為「預設」或「區塊」時, 才會出現此元素。</span><span class="sxs-lookup"><span data-stu-id="7c01d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="7c01d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c01d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c01d-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="7c01d-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="7c01d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7c01d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="7c01d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="7c01d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="7c01d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="7c01d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c01d-109">語法</span><span class="sxs-lookup"><span data-stu-id="7c01d-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c01d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c01d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7c01d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7c01d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c01d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7c01d-112">Attributes</span></span>  
  
|<span data-ttu-id="7c01d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="7c01d-113">Attribute</span></span>|<span data-ttu-id="7c01d-114">描述</span><span class="sxs-lookup"><span data-stu-id="7c01d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c01d-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="7c01d-115">chunkSize</span></span>|<span data-ttu-id="7c01d-116">任何一個 HTTP cookie 的 HTTP cookie 資料大小上限 (以字元為單位)。</span><span class="sxs-lookup"><span data-stu-id="7c01d-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="7c01d-117">調整區塊大小時, 您必須小心。</span><span class="sxs-lookup"><span data-stu-id="7c01d-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="7c01d-118">網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="7c01d-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="7c01d-119">例如, 原始的 Netscape 規格會約定這些限制:300 cookies 總計、每個 cookie 標頭4096個位元組 (包括中繼資料, 而不只是 cookie 值) 和每個網域20個 cookie。</span><span class="sxs-lookup"><span data-stu-id="7c01d-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="7c01d-120">預設值為2000。</span><span class="sxs-lookup"><span data-stu-id="7c01d-120">The default is 2000.</span></span> <span data-ttu-id="7c01d-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="7c01d-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c01d-122">子元素</span><span class="sxs-lookup"><span data-stu-id="7c01d-122">Child Elements</span></span>  
 <span data-ttu-id="7c01d-123">無</span><span class="sxs-lookup"><span data-stu-id="7c01d-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c01d-124">父項目</span><span class="sxs-lookup"><span data-stu-id="7c01d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7c01d-125">項目</span><span class="sxs-lookup"><span data-stu-id="7c01d-125">Element</span></span>|<span data-ttu-id="7c01d-126">說明</span><span class="sxs-lookup"><span data-stu-id="7c01d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c01d-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="7c01d-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="7c01d-128"><xref:System.IdentityModel.Services.CookieHandler> 設定(SAM)用來讀取<xref:System.IdentityModel.Services.SessionAuthenticationModule>和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="7c01d-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c01d-129">備註</span><span class="sxs-lookup"><span data-stu-id="7c01d-129">Remarks</span></span>  
 <span data-ttu-id="7c01d-130">當您<xref:System.IdentityModel.Services.ChunkedCookieHandler>將專案的`mode`屬性`<cookieHandler>`設定為 [預設] 或 [區塊] 時, 您可以指定 cookie 處理常式用`<chunkedCookieHandler>`來讀取和寫入 cookie 的區塊大小, 方法是包含子項目和設定其`chunkSize`屬性。</span><span class="sxs-lookup"><span data-stu-id="7c01d-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="7c01d-131">`<chunkedCookieHandler>`如果元素不存在, 則會使用預設的區塊大小2000個位元組。</span><span class="sxs-lookup"><span data-stu-id="7c01d-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="7c01d-132">當屬性設定為 "Custom" `mode`時, 無法指定此元素。</span><span class="sxs-lookup"><span data-stu-id="7c01d-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="7c01d-133">`<chunkedCookieHandler>`元素是<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="7c01d-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c01d-134">範例</span><span class="sxs-lookup"><span data-stu-id="7c01d-134">Example</span></span>  
 <span data-ttu-id="7c01d-135">下列範例會設定區塊 cookie 處理常式, 以3000個位元組的區塊寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="7c01d-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7c01d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c01d-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
