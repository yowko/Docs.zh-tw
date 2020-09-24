---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: a321c10e04eca2c1a5204929966a1725e918cbdf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158522"
---
# \<chunkedCookieHandler>

<span data-ttu-id="ab8e5-101">設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="ab8e5-102">只有當專案的 `mode` 屬性 `<cookieHandler>` 是 "Default" 或 "區塊" 時，才會出現這個元素。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="ab8e5-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab8e5-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab8e5-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab8e5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ab8e5-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab8e5-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ab8e5-106">Attributes</span></span>  
  
|<span data-ttu-id="ab8e5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ab8e5-107">Attribute</span></span>|<span data-ttu-id="ab8e5-108">描述</span><span class="sxs-lookup"><span data-stu-id="ab8e5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab8e5-109">chunkSize</span><span class="sxs-lookup"><span data-stu-id="ab8e5-109">chunkSize</span></span>|<span data-ttu-id="ab8e5-110">任何一個 HTTP cookie 的 HTTP cookie 資料大小上限（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="ab8e5-111">調整區塊大小時，您必須特別小心。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="ab8e5-112">網頁瀏覽器對於 cookie 大小和每個網域允許的數目有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="ab8e5-113">例如，原始的 Netscape 規格會約定這些限制：300個 cookie 總計、4096個位元組的每個 cookie 標頭 (包括中繼資料，而不只是) 的 cookie 值，以及每個網域20個 cookie。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="ab8e5-114">預設值為 2000。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-114">The default is 2000.</span></span> <span data-ttu-id="ab8e5-115">必要。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab8e5-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ab8e5-116">Child Elements</span></span>  

 <span data-ttu-id="ab8e5-117">無</span><span class="sxs-lookup"><span data-stu-id="ab8e5-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab8e5-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ab8e5-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab8e5-119">項目</span><span class="sxs-lookup"><span data-stu-id="ab8e5-119">Element</span></span>|<span data-ttu-id="ab8e5-120">描述</span><span class="sxs-lookup"><span data-stu-id="ab8e5-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="ab8e5-121">設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab8e5-122">備註</span><span class="sxs-lookup"><span data-stu-id="ab8e5-122">Remarks</span></span>  

 <span data-ttu-id="ab8e5-123">當您將專案的 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 屬性設定 `mode` 為「預設」或「區塊」時 `<cookieHandler>` ，可以指定 cookie 處理常式用來讀取和寫入 cookie 的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目並設定其 `chunkSize` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="ab8e5-124">如果專案 `<chunkedCookieHandler>` 不存在，則會使用預設的區塊大小2000個位元組。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="ab8e5-125">當 `mode` 屬性設定為 "Custom" 時，不能指定這個元素。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="ab8e5-126">`<chunkedCookieHandler>`元素是由 <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab8e5-127">範例</span><span class="sxs-lookup"><span data-stu-id="ab8e5-127">Example</span></span>  

 <span data-ttu-id="ab8e5-128">下列範例會設定區塊 cookie 處理常式，以3000個位元組的區塊寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="ab8e5-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab8e5-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab8e5-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
