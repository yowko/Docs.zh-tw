---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252112"
---
# \<chunkedCookieHandler>
<span data-ttu-id="197be-101">設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="197be-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="197be-102">只有當 `mode` 元素的屬性為「預設」或「區塊」時，才會出現此元素 `<cookieHandler>` 。</span><span class="sxs-lookup"><span data-stu-id="197be-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="197be-103">語法</span><span class="sxs-lookup"><span data-stu-id="197be-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="197be-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="197be-104">Attributes and Elements</span></span>  
 <span data-ttu-id="197be-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="197be-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="197be-106">屬性</span><span class="sxs-lookup"><span data-stu-id="197be-106">Attributes</span></span>  
  
|<span data-ttu-id="197be-107">屬性</span><span class="sxs-lookup"><span data-stu-id="197be-107">Attribute</span></span>|<span data-ttu-id="197be-108">描述</span><span class="sxs-lookup"><span data-stu-id="197be-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="197be-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="197be-109">chunkSize</span></span>|<span data-ttu-id="197be-110">任何一個 HTTP cookie 的 HTTP cookie 資料大小上限（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="197be-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="197be-111">調整區塊大小時，您必須小心。</span><span class="sxs-lookup"><span data-stu-id="197be-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="197be-112">網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="197be-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="197be-113">例如，原始的 Netscape 規格會約定這些限制： 300 cookies 總計、每個 cookie 標頭4096個位元組（包括中繼資料，而不只是 cookie 值）和每個網域20個 cookie。</span><span class="sxs-lookup"><span data-stu-id="197be-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="197be-114">預設值為 2000。</span><span class="sxs-lookup"><span data-stu-id="197be-114">The default is 2000.</span></span> <span data-ttu-id="197be-115">必要。</span><span class="sxs-lookup"><span data-stu-id="197be-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="197be-116">子元素</span><span class="sxs-lookup"><span data-stu-id="197be-116">Child Elements</span></span>  
 <span data-ttu-id="197be-117">無</span><span class="sxs-lookup"><span data-stu-id="197be-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="197be-118">父項目</span><span class="sxs-lookup"><span data-stu-id="197be-118">Parent Elements</span></span>  
  
|<span data-ttu-id="197be-119">元素</span><span class="sxs-lookup"><span data-stu-id="197be-119">Element</span></span>|<span data-ttu-id="197be-120">描述</span><span class="sxs-lookup"><span data-stu-id="197be-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="197be-121">設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）用來讀取和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="197be-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="197be-122">備註</span><span class="sxs-lookup"><span data-stu-id="197be-122">Remarks</span></span>  
 <span data-ttu-id="197be-123">當您將專案 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 的屬性設定 `mode` `<cookieHandler>` 為 [預設] 或 [區塊] 時，可以指定 cookie 處理常式用來讀取和寫入 cookie 的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目並設定其 `chunkSize` 屬性。</span><span class="sxs-lookup"><span data-stu-id="197be-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="197be-124">如果 `<chunkedCookieHandler>` 元素不存在，則會使用預設的區塊大小2000個位元組。</span><span class="sxs-lookup"><span data-stu-id="197be-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="197be-125">當 `mode` 屬性設定為 "Custom" 時，無法指定此元素。</span><span class="sxs-lookup"><span data-stu-id="197be-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="197be-126">`<chunkedCookieHandler>`元素是由 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="197be-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="197be-127">範例</span><span class="sxs-lookup"><span data-stu-id="197be-127">Example</span></span>  
 <span data-ttu-id="197be-128">下列範例會設定區塊 cookie 處理常式，以3000個位元組的區塊寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="197be-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="197be-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="197be-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
