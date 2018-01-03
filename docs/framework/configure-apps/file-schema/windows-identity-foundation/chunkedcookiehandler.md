---
title: '&lt;chunkedCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c5d526ccd48ea5e822d5d29fb38dacd895c2556c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="3e93b-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="3e93b-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="3e93b-103">設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。</span><span class="sxs-lookup"><span data-stu-id="3e93b-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="3e93b-104">這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`元素是 「 預設 」 或 「 區塊 」。</span><span class="sxs-lookup"><span data-stu-id="3e93b-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="3e93b-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="3e93b-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="3e93b-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3e93b-106">\<federationConfiguration></span></span>  
<span data-ttu-id="3e93b-107">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="3e93b-107">\<cookieHandler></span></span>  
<span data-ttu-id="3e93b-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="3e93b-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e93b-109">語法</span><span class="sxs-lookup"><span data-stu-id="3e93b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e93b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3e93b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e93b-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3e93b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e93b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3e93b-112">Attributes</span></span>  
  
|<span data-ttu-id="3e93b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3e93b-113">Attribute</span></span>|<span data-ttu-id="3e93b-114">描述</span><span class="sxs-lookup"><span data-stu-id="3e93b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e93b-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="3e93b-115">chunkSize</span></span>|<span data-ttu-id="3e93b-116">大小上限，以字元為單位的任何一個 HTTP cookie 的 HTTP cookie 資料。</span><span class="sxs-lookup"><span data-stu-id="3e93b-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="3e93b-117">您必須小心時調整的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="3e93b-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="3e93b-118">網頁瀏覽器的 cookie 和每個網域的允許數目大小有不同的限制。</span><span class="sxs-lookup"><span data-stu-id="3e93b-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="3e93b-119">例如，原始的 Netscape 規格約定這些限制： 300 cookie 加總，4096 個位元組，每個 cookie 標頭 （包括中繼資料，不只是 cookie 的值） 和每個網域的 20 cookie。</span><span class="sxs-lookup"><span data-stu-id="3e93b-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="3e93b-120">預設值是 2000年。</span><span class="sxs-lookup"><span data-stu-id="3e93b-120">The default is 2000.</span></span> <span data-ttu-id="3e93b-121">必要。</span><span class="sxs-lookup"><span data-stu-id="3e93b-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e93b-122">子元素</span><span class="sxs-lookup"><span data-stu-id="3e93b-122">Child Elements</span></span>  
 <span data-ttu-id="3e93b-123">無</span><span class="sxs-lookup"><span data-stu-id="3e93b-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e93b-124">父項目</span><span class="sxs-lookup"><span data-stu-id="3e93b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3e93b-125">項目</span><span class="sxs-lookup"><span data-stu-id="3e93b-125">Element</span></span>|<span data-ttu-id="3e93b-126">描述</span><span class="sxs-lookup"><span data-stu-id="3e93b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e93b-127">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="3e93b-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="3e93b-128">設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="3e93b-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e93b-129">備註</span><span class="sxs-lookup"><span data-stu-id="3e93b-129">Remarks</span></span>  
 <span data-ttu-id="3e93b-130">當您指定<xref:System.IdentityModel.Services.ChunkedCookieHandler>藉由設定`mode`屬性`<cookieHandler>`"Default"或"Chunked"的項目，您可以指定區塊大小的 cookie 處理常式用來讀取和寫入，藉以 cookie`<chunkedCookieHandler>`子項目和設定其`chunkSize`屬性。</span><span class="sxs-lookup"><span data-stu-id="3e93b-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="3e93b-131">如果`<chunkedCookieHandler>`項目不存在，使用預設區塊大小為 2000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="3e93b-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="3e93b-132">此元素不能指定何時`mode`屬性設為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="3e93b-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="3e93b-133">`<chunkedCookieHandler>`項目由<xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>類別。</span><span class="sxs-lookup"><span data-stu-id="3e93b-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e93b-134">範例</span><span class="sxs-lookup"><span data-stu-id="3e93b-134">Example</span></span>  
 <span data-ttu-id="3e93b-135">下列範例會設定會將 cookie 寫入 3000 位元組的區塊的區塊的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="3e93b-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e93b-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e93b-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
