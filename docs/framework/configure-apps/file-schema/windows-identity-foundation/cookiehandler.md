---
title: '&lt;Requiressl&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 88e968d025c959ec33674a9d8edb5e63341433ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcookiehandlergt"></a><span data-ttu-id="059ff-102">&lt;Requiressl&gt;</span><span class="sxs-lookup"><span data-stu-id="059ff-102">&lt;cookieHandler&gt;</span></span>
<span data-ttu-id="059ff-103">設定<xref:System.IdentityModel.Services.CookieHandler>， <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 用來讀取和寫入 cookie。</span><span class="sxs-lookup"><span data-stu-id="059ff-103">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>  
  
 <span data-ttu-id="059ff-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="059ff-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="059ff-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="059ff-105">\<federationConfiguration></span></span>  
<span data-ttu-id="059ff-106">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="059ff-106">\<cookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="059ff-107">語法</span><span class="sxs-lookup"><span data-stu-id="059ff-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler name=xs:string  
        path=Path  
        mode="Chunked||Custom||Default"  
        persistentSessionLifetime=xs:string  
        hideFromScript=xs:boolean  
        requireSSL=xs:boolean  
        domain=xs:string  
      <chunkedCookieHandler size=xs:int />  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="059ff-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="059ff-108">Attributes and Elements</span></span>  
 <span data-ttu-id="059ff-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="059ff-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="059ff-110">屬性</span><span class="sxs-lookup"><span data-stu-id="059ff-110">Attributes</span></span>  
  
|<span data-ttu-id="059ff-111">屬性</span><span class="sxs-lookup"><span data-stu-id="059ff-111">Attribute</span></span>|<span data-ttu-id="059ff-112">描述</span><span class="sxs-lookup"><span data-stu-id="059ff-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="059ff-113">name</span><span class="sxs-lookup"><span data-stu-id="059ff-113">name</span></span>|<span data-ttu-id="059ff-114">指定寫入任何 cookie 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="059ff-114">Specifies the base name for any cookies written.</span></span> <span data-ttu-id="059ff-115">預設為"FedAuth"。</span><span class="sxs-lookup"><span data-stu-id="059ff-115">The default is "FedAuth".</span></span>|  
|<span data-ttu-id="059ff-116">路徑</span><span class="sxs-lookup"><span data-stu-id="059ff-116">path</span></span>|<span data-ttu-id="059ff-117">指定寫入任何 cookie 的路徑值。</span><span class="sxs-lookup"><span data-stu-id="059ff-117">Specifies the path value for any cookies written.</span></span> <span data-ttu-id="059ff-118">預設為"HttpRuntime.AppDomainAppVirtualPath"。</span><span class="sxs-lookup"><span data-stu-id="059ff-118">The default is "HttpRuntime.AppDomainAppVirtualPath".</span></span>|  
|<span data-ttu-id="059ff-119">模式</span><span class="sxs-lookup"><span data-stu-id="059ff-119">mode</span></span>|<span data-ttu-id="059ff-120">其中一個<xref:System.IdentityModel.Services.CookieHandlerMode>值，指定 SAM 所使用的 cookie 處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="059ff-120">One of the <xref:System.IdentityModel.Services.CookieHandlerMode> values that specifies the kind of cookie handler used by the SAM.</span></span> <span data-ttu-id="059ff-121">可以使用下列值：</span><span class="sxs-lookup"><span data-stu-id="059ff-121">The following values may be used:</span></span><br /><br /> <span data-ttu-id="059ff-122">-"Default"-"Chunked"相同。</span><span class="sxs-lookup"><span data-stu-id="059ff-122">-   "Default" — The same as "Chunked".</span></span><br /><span data-ttu-id="059ff-123">-「 區塊 」，在使用執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="059ff-123">-   "Chunked" — Uses an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="059ff-124">此 cookie 處理常式可確保個別 cookie 不會超過設定的最大大小。</span><span class="sxs-lookup"><span data-stu-id="059ff-124">This cookie handler ensures that individual cookies do not exceed a set maximum size.</span></span> <span data-ttu-id="059ff-125">它是由潛在"區塊處理 「 邏輯 cookie 成數個 cookie 在線上完成此動作。</span><span class="sxs-lookup"><span data-stu-id="059ff-125">It accomplishes this by potentially "chunking" one logical cookie into a number of cookies on-the-wire.</span></span><br /><span data-ttu-id="059ff-126">-"Custom"，在使用衍生自的自訂類別執行個體<xref:System.IdentityModel.Services.CookieHandler>。</span><span class="sxs-lookup"><span data-stu-id="059ff-126">-   "Custom" — Uses an instance of a custom class derived from <xref:System.IdentityModel.Services.CookieHandler>.</span></span> <span data-ttu-id="059ff-127">在衍生的類別由參考`<customCookieHandler>`子項目。</span><span class="sxs-lookup"><span data-stu-id="059ff-127">The derived class is referenced by the `<customCookieHandler>` child element.</span></span><br /><br /> <span data-ttu-id="059ff-128">預設為 「 預設 」。</span><span class="sxs-lookup"><span data-stu-id="059ff-128">The default is "Default".</span></span>|  
|<span data-ttu-id="059ff-129">persistentSessionLifetime</span><span class="sxs-lookup"><span data-stu-id="059ff-129">persistentSessionLifetime</span></span>|<span data-ttu-id="059ff-130">指定持續性工作階段的存留期。</span><span class="sxs-lookup"><span data-stu-id="059ff-130">Specifies the lifetime of persistent sessions.</span></span> <span data-ttu-id="059ff-131">如果是零，一律使用暫時性工作階段。</span><span class="sxs-lookup"><span data-stu-id="059ff-131">If zero, transient sessions are always used.</span></span> <span data-ttu-id="059ff-132">預設值是"0:0:0"，其指定的暫時性工作階段。</span><span class="sxs-lookup"><span data-stu-id="059ff-132">The default value is "0:0:0", which specifies a transient session.</span></span> <span data-ttu-id="059ff-133">最大值是"365:0:0"，其指定為 365 天的工作階段。</span><span class="sxs-lookup"><span data-stu-id="059ff-133">The maximum value is "365:0:0", which specifies a session of 365 days.</span></span> <span data-ttu-id="059ff-134">應該指定的值，根據下列限制： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`，其中最左邊的值會指定天數、 中間值 （如果有的話） 會指定小時，而將分鐘指定的最右方值 （如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="059ff-134">The value should be specified according to the following restriction: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, where the leftmost value specifies days, the middle value (if present) specifies hours, and the rightmost value (if present) specifies minutes.</span></span>|  
|<span data-ttu-id="059ff-135">RequireSsl</span><span class="sxs-lookup"><span data-stu-id="059ff-135">requireSsl</span></span>|<span data-ttu-id="059ff-136">指定是否為任何撰寫的 cookie 發出"Secure"旗標。</span><span class="sxs-lookup"><span data-stu-id="059ff-136">Specifies whether the "Secure" flag is emitted for any cookies written.</span></span> <span data-ttu-id="059ff-137">如果此值設定時，登入工作階段 cookie 只能使用透過 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="059ff-137">If this value is set, the sign-in session cookies will only be available over HTTPS.</span></span> <span data-ttu-id="059ff-138">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="059ff-138">The default is "true".</span></span>|  
|<span data-ttu-id="059ff-139">hideFromScript</span><span class="sxs-lookup"><span data-stu-id="059ff-139">hideFromScript</span></span>|<span data-ttu-id="059ff-140">控制是否為任何撰寫的 cookie 發出"HttpOnly 」 旗標。</span><span class="sxs-lookup"><span data-stu-id="059ff-140">Controls whether the "HttpOnly" flag is emitted for any cookies written.</span></span> <span data-ttu-id="059ff-141">某些網頁瀏覽器接受這個旗標會保留用戶端指令碼存取 cookie 值。</span><span class="sxs-lookup"><span data-stu-id="059ff-141">Certain web browsers honor this flag by keeping client-side script from accessing the cookie value.</span></span> <span data-ttu-id="059ff-142">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="059ff-142">The default is "true".</span></span>|  
|<span data-ttu-id="059ff-143">網域</span><span class="sxs-lookup"><span data-stu-id="059ff-143">domain</span></span>|<span data-ttu-id="059ff-144">寫入任何 cookie 網域值。</span><span class="sxs-lookup"><span data-stu-id="059ff-144">The domain value for any cookies written.</span></span> <span data-ttu-id="059ff-145">預設值為 ""。</span><span class="sxs-lookup"><span data-stu-id="059ff-145">The default is "".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="059ff-146">子元素</span><span class="sxs-lookup"><span data-stu-id="059ff-146">Child Elements</span></span>  
  
|<span data-ttu-id="059ff-147">項目</span><span class="sxs-lookup"><span data-stu-id="059ff-147">Element</span></span>|<span data-ttu-id="059ff-148">說明</span><span class="sxs-lookup"><span data-stu-id="059ff-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="059ff-149">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="059ff-149">\<chunkedCookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/chunkedcookiehandler.md)|<span data-ttu-id="059ff-150">設定<xref:System.IdentityModel.Services.ChunkedCookieHandler>。</span><span class="sxs-lookup"><span data-stu-id="059ff-150">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="059ff-151">這個項目可能只會存在於如果`mode`屬性`<cookieHandler>`元素是 「 預設 」 或 「 區塊 」。</span><span class="sxs-lookup"><span data-stu-id="059ff-151">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>|  
|[<span data-ttu-id="059ff-152">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="059ff-152">\<customCookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/customcookiehandler.md)|<span data-ttu-id="059ff-153">設定自訂的 cookie 處理常式型別。</span><span class="sxs-lookup"><span data-stu-id="059ff-153">Sets the custom cookie handler type.</span></span> <span data-ttu-id="059ff-154">必須有此項目如果`mode`屬性`<cookieHandler>`項目是 「 自訂 」。</span><span class="sxs-lookup"><span data-stu-id="059ff-154">This element must be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="059ff-155">它不能存在的任何其他值`mode`屬性。</span><span class="sxs-lookup"><span data-stu-id="059ff-155">It cannot be present for any other values of the `mode` attribute.</span></span> <span data-ttu-id="059ff-156">自訂型別必須衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="059ff-156">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="059ff-157">父項目</span><span class="sxs-lookup"><span data-stu-id="059ff-157">Parent Elements</span></span>  
  
|<span data-ttu-id="059ff-158">項目</span><span class="sxs-lookup"><span data-stu-id="059ff-158">Element</span></span>|<span data-ttu-id="059ff-159">說明</span><span class="sxs-lookup"><span data-stu-id="059ff-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="059ff-160">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="059ff-160">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="059ff-161">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="059ff-161">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="059ff-162">備註</span><span class="sxs-lookup"><span data-stu-id="059ff-162">Remarks</span></span>  
 <span data-ttu-id="059ff-163"><xref:System.IdentityModel.Services.CookieHandler>負責讀取和寫入未經處理的 cookie，在 HTTP 通訊協定層級。</span><span class="sxs-lookup"><span data-stu-id="059ff-163">The <xref:System.IdentityModel.Services.CookieHandler> is responsible for reading and writing raw cookies at the HTTP protocol level.</span></span> <span data-ttu-id="059ff-164">您可以設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler>或自訂的 cookie 處理常式衍生自<xref:System.IdentityModel.Services.CookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="059ff-164">You can configure either a <xref:System.IdentityModel.Services.ChunkedCookieHandler> or a custom cookie handler derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="059ff-165">若要設定的區塊的 cookie 處理常式，模式將屬性設定為"Chunked"或"Default"。</span><span class="sxs-lookup"><span data-stu-id="059ff-165">To configure a chunked cookie handler, set the mode attribute to "Chunked" or "Default".</span></span> <span data-ttu-id="059ff-166">預設區塊大小為 2000 個位元組，但您可以選擇性地藉由指定不同的區塊大小`<chunkedCookieHandler>`子項目。</span><span class="sxs-lookup"><span data-stu-id="059ff-166">The default chunk size is 2000 bytes, but you may optionally specify a different chunk size by including a `<chunkedCookieHandler>` child element.</span></span>  
  
 <span data-ttu-id="059ff-167">若要設定自訂的 cookie 處理常式，模式將屬性設定為"Custom"。</span><span class="sxs-lookup"><span data-stu-id="059ff-167">To configure a custom cookie handler, set the mode attribute to "Custom".</span></span> <span data-ttu-id="059ff-168">您也必須指定`<customCookieHandler>`子項目會參考您的自訂處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="059ff-168">You must also specify a `<customCookieHandler>` child element that references the type of your custom handler.</span></span>  
  
 <span data-ttu-id="059ff-169">`<cookieHandler>`項目由<xref:System.IdentityModel.Services.CookieHandlerElement>類別。</span><span class="sxs-lookup"><span data-stu-id="059ff-169">The `<cookieHandler>` element is represented by the <xref:System.IdentityModel.Services.CookieHandlerElement> class.</span></span> <span data-ttu-id="059ff-170">已在組態中指定的 cookie 處理常式是可從<xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A>屬性<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件上設定<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="059ff-170">The cookie handler that was specified in configuration is available from the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> property of the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="059ff-171">範例</span><span class="sxs-lookup"><span data-stu-id="059ff-171">Example</span></span>  
 <span data-ttu-id="059ff-172">下列 XML 會說明`<cookieHandler>`項目。</span><span class="sxs-lookup"><span data-stu-id="059ff-172">The following XML shows a `<cookieHandler>` element.</span></span> <span data-ttu-id="059ff-173">在此範例中，因為`mode`屬性未指定，SAM 將使用預設的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="059ff-173">In this example, because the `mode` attribute is not specified, the default cookie handler will be used by the SAM.</span></span> <span data-ttu-id="059ff-174">這是執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="059ff-174">This is an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="059ff-175">因為`<chunkedCookieHandler>`未指定子元素，將使用預設區塊大小。</span><span class="sxs-lookup"><span data-stu-id="059ff-175">Because the `<chunkedCookieHandler>` child element is not specified, the default chunk size will be used.</span></span> <span data-ttu-id="059ff-176">不需要 HTTPS，因為`requireSsl`屬性設定`false`。</span><span class="sxs-lookup"><span data-stu-id="059ff-176">HTTPS will not be required because the `requireSsl` attribute is set `false`.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="059ff-177">在此範例中，不需要 HTTPS 來撰寫工作階段 cookie。</span><span class="sxs-lookup"><span data-stu-id="059ff-177">In this example, HTTPS is not required to write session cookies.</span></span> <span data-ttu-id="059ff-178">這是因為`requireSsl`屬性`<cookieHandler>`元素設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="059ff-178">This is because the `requireSsl` attribute on the `<cookieHandler>` element is set to `false`.</span></span> <span data-ttu-id="059ff-179">這項設定不會建議針對大部分的實際執行環境，因為它可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="059ff-179">This setting is not recommended for most production environments as it may present a security risk.</span></span>  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="059ff-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="059ff-180">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>
