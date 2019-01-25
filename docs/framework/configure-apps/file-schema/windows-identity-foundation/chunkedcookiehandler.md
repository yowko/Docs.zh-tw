---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 1726d4ade9405543bdfdb4e4803f87f258de791e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691277"
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="93b9c-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="93b9c-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="93b9c-103">設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。</span><span class="sxs-lookup"><span data-stu-id="93b9c-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="93b9c-104">這個項目只會出現如果`mode`屬性的`<cookieHandler>`項目是 「 預設 」 或 「 區塊 」。</span><span class="sxs-lookup"><span data-stu-id="93b9c-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="93b9c-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="93b9c-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="93b9c-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="93b9c-106">\<federationConfiguration></span></span>  
<span data-ttu-id="93b9c-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="93b9c-107">\<cookieHandler></span></span>  
<span data-ttu-id="93b9c-108">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="93b9c-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b9c-109">語法</span><span class="sxs-lookup"><span data-stu-id="93b9c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93b9c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93b9c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93b9c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93b9c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93b9c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="93b9c-112">Attributes</span></span>  
  
|<span data-ttu-id="93b9c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="93b9c-113">Attribute</span></span>|<span data-ttu-id="93b9c-114">描述</span><span class="sxs-lookup"><span data-stu-id="93b9c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93b9c-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="93b9c-115">chunkSize</span></span>|<span data-ttu-id="93b9c-116">最大的大小，以字元為單位的任何一個的 HTTP cookie 的 HTTP cookie 資料。</span><span class="sxs-lookup"><span data-stu-id="93b9c-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="93b9c-117">您必須小心調整區塊大小。</span><span class="sxs-lookup"><span data-stu-id="93b9c-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="93b9c-118">網頁瀏覽器 cookie 和每一個網域允許的數字的大小有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="93b9c-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="93b9c-119">例如，原始的 Netscape 規格約定這些限制：4096 個位元組，每個 cookie 標頭 （包括中繼資料，不只是 cookie 值），以及每個網域的 20 cookie 總 300 的 cookie。</span><span class="sxs-lookup"><span data-stu-id="93b9c-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="93b9c-120">預設值是 2000年。</span><span class="sxs-lookup"><span data-stu-id="93b9c-120">The default is 2000.</span></span> <span data-ttu-id="93b9c-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="93b9c-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93b9c-122">子元素</span><span class="sxs-lookup"><span data-stu-id="93b9c-122">Child Elements</span></span>  
 <span data-ttu-id="93b9c-123">無</span><span class="sxs-lookup"><span data-stu-id="93b9c-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93b9c-124">父項目</span><span class="sxs-lookup"><span data-stu-id="93b9c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="93b9c-125">項目</span><span class="sxs-lookup"><span data-stu-id="93b9c-125">Element</span></span>|<span data-ttu-id="93b9c-126">描述</span><span class="sxs-lookup"><span data-stu-id="93b9c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93b9c-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="93b9c-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="93b9c-128">會設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 會使用來讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="93b9c-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b9c-129">備註</span><span class="sxs-lookup"><span data-stu-id="93b9c-129">Remarks</span></span>  
 <span data-ttu-id="93b9c-130">當您指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>splittunneling`mode`屬性`<cookieHandler>`"Default"或"Chunked"的項目，您可以指定區塊大小的 cookie 處理常式用來讀取和寫入 cookie 包括`<chunkedCookieHandler>`子項目和設定其`chunkSize`屬性。</span><span class="sxs-lookup"><span data-stu-id="93b9c-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="93b9c-131">如果`<chunkedCookieHandler>`項目不存在，使用 2000 個位元組的預設區塊大小。</span><span class="sxs-lookup"><span data-stu-id="93b9c-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="93b9c-132">此元素不能指定何時`mode`屬性設為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="93b9c-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="93b9c-133">`<chunkedCookieHandler>`項目由<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>類別。</span><span class="sxs-lookup"><span data-stu-id="93b9c-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93b9c-134">範例</span><span class="sxs-lookup"><span data-stu-id="93b9c-134">Example</span></span>  
 <span data-ttu-id="93b9c-135">下列範例會設定區塊的 cookie 處理常式會將 cookie 寫入以 3000 位元組的區塊。</span><span class="sxs-lookup"><span data-stu-id="93b9c-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="93b9c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93b9c-136">See also</span></span>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
