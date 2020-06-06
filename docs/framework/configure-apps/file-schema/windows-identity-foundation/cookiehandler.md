---
title: <cookieHandler>
ms.date: 03/30/2017
ms.assetid: bfdc127f-8d94-4566-8bef-f583c6ae7398
author: BrucePerlerMS
ms.openlocfilehash: 853dc9817d080e59ac7a792576eda862bd0b1f1d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252032"
---
# \<cookieHandler>
<span data-ttu-id="e125a-101">設定 <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）用來讀取和寫入 cookie 的。</span><span class="sxs-lookup"><span data-stu-id="e125a-101">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="e125a-102">語法</span><span class="sxs-lookup"><span data-stu-id="e125a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e125a-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e125a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e125a-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e125a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e125a-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e125a-105">Attributes</span></span>  
  
|<span data-ttu-id="e125a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e125a-106">Attribute</span></span>|<span data-ttu-id="e125a-107">描述</span><span class="sxs-lookup"><span data-stu-id="e125a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e125a-108">NAME</span><span class="sxs-lookup"><span data-stu-id="e125a-108">name</span></span>|<span data-ttu-id="e125a-109">指定任何寫入 cookie 的基底名稱。</span><span class="sxs-lookup"><span data-stu-id="e125a-109">Specifies the base name for any cookies written.</span></span> <span data-ttu-id="e125a-110">預設值為 "FedAuth"。</span><span class="sxs-lookup"><span data-stu-id="e125a-110">The default is "FedAuth".</span></span>|  
|<span data-ttu-id="e125a-111">路徑</span><span class="sxs-lookup"><span data-stu-id="e125a-111">path</span></span>|<span data-ttu-id="e125a-112">指定任何寫入 cookie 的路徑值。</span><span class="sxs-lookup"><span data-stu-id="e125a-112">Specifies the path value for any cookies written.</span></span> <span data-ttu-id="e125a-113">預設值為 "HttpRuntime. AppDomainAppVirtualPath"。</span><span class="sxs-lookup"><span data-stu-id="e125a-113">The default is "HttpRuntime.AppDomainAppVirtualPath".</span></span>|  
|<span data-ttu-id="e125a-114">mode</span><span class="sxs-lookup"><span data-stu-id="e125a-114">mode</span></span>|<span data-ttu-id="e125a-115">其中一個 <xref:System.IdentityModel.Services.CookieHandlerMode> 值，指定 SAM 所使用的 cookie 處理常式種類。</span><span class="sxs-lookup"><span data-stu-id="e125a-115">One of the <xref:System.IdentityModel.Services.CookieHandlerMode> values that specifies the kind of cookie handler used by the SAM.</span></span> <span data-ttu-id="e125a-116">可能會使用下列值：</span><span class="sxs-lookup"><span data-stu-id="e125a-116">The following values may be used:</span></span><br /><br /> <span data-ttu-id="e125a-117">-「預設」-與「區塊」相同。</span><span class="sxs-lookup"><span data-stu-id="e125a-117">-   "Default" — The same as "Chunked".</span></span><br /><span data-ttu-id="e125a-118">-「區塊」-使用類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-118">-   "Chunked" — Uses an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="e125a-119">此 cookie 處理常式可確保個別 cookie 不會超過設定的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e125a-119">This cookie handler ensures that individual cookies do not exceed a set maximum size.</span></span> <span data-ttu-id="e125a-120">這是因為可能會將一個邏輯 cookie 「區塊化」到多個網路上的 cookie。</span><span class="sxs-lookup"><span data-stu-id="e125a-120">It accomplishes this by potentially "chunking" one logical cookie into a number of cookies on-the-wire.</span></span><br /><span data-ttu-id="e125a-121">-「自訂」—使用衍生自之自訂類別的實例 <xref:System.IdentityModel.Services.CookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-121">-   "Custom" — Uses an instance of a custom class derived from <xref:System.IdentityModel.Services.CookieHandler>.</span></span> <span data-ttu-id="e125a-122">衍生類別是由 `<customCookieHandler>` 子項目所參考。</span><span class="sxs-lookup"><span data-stu-id="e125a-122">The derived class is referenced by the `<customCookieHandler>` child element.</span></span><br /><br /> <span data-ttu-id="e125a-123">預設值為 "Default"。</span><span class="sxs-lookup"><span data-stu-id="e125a-123">The default is "Default".</span></span>|  
|<span data-ttu-id="e125a-124">persistentSessionLifetime</span><span class="sxs-lookup"><span data-stu-id="e125a-124">persistentSessionLifetime</span></span>|<span data-ttu-id="e125a-125">指定持續性會話的存留期。</span><span class="sxs-lookup"><span data-stu-id="e125a-125">Specifies the lifetime of persistent sessions.</span></span> <span data-ttu-id="e125a-126">如果是零，則永遠使用暫時性工作階段。</span><span class="sxs-lookup"><span data-stu-id="e125a-126">If zero, transient sessions are always used.</span></span> <span data-ttu-id="e125a-127">預設值為 "0:0:0"，指定暫時性會話。</span><span class="sxs-lookup"><span data-stu-id="e125a-127">The default value is "0:0:0", which specifies a transient session.</span></span> <span data-ttu-id="e125a-128">最大值為 "365:0:0"，指定365天的會話。</span><span class="sxs-lookup"><span data-stu-id="e125a-128">The maximum value is "365:0:0", which specifies a session of 365 days.</span></span> <span data-ttu-id="e125a-129">應該根據下列限制來指定值： `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />` ，其中最左邊的值會指定 days、中間值（如果有的話）指定小時，而最右邊的值（如果有的話）會指定分鐘。</span><span class="sxs-lookup"><span data-stu-id="e125a-129">The value should be specified according to the following restriction: `<xs:pattern value="([0-9.]+:){0,1}([0-9]+:){0,1}[0-9.]+" />`, where the leftmost value specifies days, the middle value (if present) specifies hours, and the rightmost value (if present) specifies minutes.</span></span>|  
|<span data-ttu-id="e125a-130">requireSsl</span><span class="sxs-lookup"><span data-stu-id="e125a-130">requireSsl</span></span>|<span data-ttu-id="e125a-131">指定是否針對任何寫入的 cookie 發出 "Secure" 旗標。</span><span class="sxs-lookup"><span data-stu-id="e125a-131">Specifies whether the "Secure" flag is emitted for any cookies written.</span></span> <span data-ttu-id="e125a-132">如果設定此值，登入會話 cookie 只會透過 HTTPS 提供。</span><span class="sxs-lookup"><span data-stu-id="e125a-132">If this value is set, the sign-in session cookies will only be available over HTTPS.</span></span> <span data-ttu-id="e125a-133">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="e125a-133">The default is "true".</span></span>|  
|<span data-ttu-id="e125a-134">hideFromScript</span><span class="sxs-lookup"><span data-stu-id="e125a-134">hideFromScript</span></span>|<span data-ttu-id="e125a-135">控制是否針對任何寫入的 cookie 發出 "HttpOnly" 旗標。</span><span class="sxs-lookup"><span data-stu-id="e125a-135">Controls whether the "HttpOnly" flag is emitted for any cookies written.</span></span> <span data-ttu-id="e125a-136">某些網頁瀏覽器會藉由保留用戶端腳本來存取 cookie 值，以接受此旗標。</span><span class="sxs-lookup"><span data-stu-id="e125a-136">Certain web browsers honor this flag by keeping client-side script from accessing the cookie value.</span></span> <span data-ttu-id="e125a-137">預設為 "true"。</span><span class="sxs-lookup"><span data-stu-id="e125a-137">The default is "true".</span></span>|  
|<span data-ttu-id="e125a-138">網域</span><span class="sxs-lookup"><span data-stu-id="e125a-138">domain</span></span>|<span data-ttu-id="e125a-139">任何寫入 cookie 的網域值。</span><span class="sxs-lookup"><span data-stu-id="e125a-139">The domain value for any cookies written.</span></span> <span data-ttu-id="e125a-140">預設值為 ""。</span><span class="sxs-lookup"><span data-stu-id="e125a-140">The default is "".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e125a-141">子元素</span><span class="sxs-lookup"><span data-stu-id="e125a-141">Child Elements</span></span>  
  
|<span data-ttu-id="e125a-142">元素</span><span class="sxs-lookup"><span data-stu-id="e125a-142">Element</span></span>|<span data-ttu-id="e125a-143">描述</span><span class="sxs-lookup"><span data-stu-id="e125a-143">Description</span></span>|  
|-------------|-----------------|  
|[\<chunkedCookieHandler>](chunkedcookiehandler.md)|<span data-ttu-id="e125a-144">設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-144">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="e125a-145">只有當 `mode` 元素的屬性為「預設」或「區塊」時，才會出現此元素 `<cookieHandler>` 。</span><span class="sxs-lookup"><span data-stu-id="e125a-145">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>|  
|[\<customCookieHandler>](customcookiehandler.md)|<span data-ttu-id="e125a-146">設定自訂 cookie 處理常式類型。</span><span class="sxs-lookup"><span data-stu-id="e125a-146">Sets the custom cookie handler type.</span></span> <span data-ttu-id="e125a-147">如果 `mode` 元素的屬性 `<cookieHandler>` 為 "Custom"，則必須要有此元素。</span><span class="sxs-lookup"><span data-stu-id="e125a-147">This element must be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="e125a-148">它不能存在於屬性的任何其他值 `mode` 。</span><span class="sxs-lookup"><span data-stu-id="e125a-148">It cannot be present for any other values of the `mode` attribute.</span></span> <span data-ttu-id="e125a-149">自訂類型必須衍生自 <xref:System.IdentityModel.Services.CookieHandler> 類別。</span><span class="sxs-lookup"><span data-stu-id="e125a-149">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e125a-150">父項目</span><span class="sxs-lookup"><span data-stu-id="e125a-150">Parent Elements</span></span>  
  
|<span data-ttu-id="e125a-151">元素</span><span class="sxs-lookup"><span data-stu-id="e125a-151">Element</span></span>|<span data-ttu-id="e125a-152">描述</span><span class="sxs-lookup"><span data-stu-id="e125a-152">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="e125a-153">包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的設定。</span><span class="sxs-lookup"><span data-stu-id="e125a-153">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e125a-154">備註</span><span class="sxs-lookup"><span data-stu-id="e125a-154">Remarks</span></span>  
 <span data-ttu-id="e125a-155"><xref:System.IdentityModel.Services.CookieHandler>負責讀取及寫入 HTTP 通訊協定層級的原始 cookie。</span><span class="sxs-lookup"><span data-stu-id="e125a-155">The <xref:System.IdentityModel.Services.CookieHandler> is responsible for reading and writing raw cookies at the HTTP protocol level.</span></span> <span data-ttu-id="e125a-156">您可以設定 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 從類別衍生的或自訂 cookie 處理常式 <xref:System.IdentityModel.Services.CookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-156">You can configure either a <xref:System.IdentityModel.Services.ChunkedCookieHandler> or a custom cookie handler derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="e125a-157">若要設定區塊 cookie 處理常式，請將 mode 屬性設為 "分塊" 或 "Default"。</span><span class="sxs-lookup"><span data-stu-id="e125a-157">To configure a chunked cookie handler, set the mode attribute to "Chunked" or "Default".</span></span> <span data-ttu-id="e125a-158">預設的區塊大小是2000個位元組，但是您可以選擇性地指定不同的區塊大小，方法是包含 `<chunkedCookieHandler>` 子項目。</span><span class="sxs-lookup"><span data-stu-id="e125a-158">The default chunk size is 2000 bytes, but you may optionally specify a different chunk size by including a `<chunkedCookieHandler>` child element.</span></span>  
  
 <span data-ttu-id="e125a-159">若要設定自訂的 cookie 處理常式，請將 mode 屬性設為 "Custom"。</span><span class="sxs-lookup"><span data-stu-id="e125a-159">To configure a custom cookie handler, set the mode attribute to "Custom".</span></span> <span data-ttu-id="e125a-160">您也必須指定 `<customCookieHandler>` 參考自訂處理常式類型的子項目。</span><span class="sxs-lookup"><span data-stu-id="e125a-160">You must also specify a `<customCookieHandler>` child element that references the type of your custom handler.</span></span>  
  
 <span data-ttu-id="e125a-161">`<cookieHandler>`元素是由 <xref:System.IdentityModel.Services.CookieHandlerElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="e125a-161">The `<cookieHandler>` element is represented by the <xref:System.IdentityModel.Services.CookieHandlerElement> class.</span></span> <span data-ttu-id="e125a-162">在設定中指定的 cookie 處理常式，可從 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上物件集的屬性取得 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-162">The cookie handler that was specified in configuration is available from the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration.CookieHandler%2A> property of the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e125a-163">範例</span><span class="sxs-lookup"><span data-stu-id="e125a-163">Example</span></span>  
 <span data-ttu-id="e125a-164">下列 XML 會顯示 `<cookieHandler>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e125a-164">The following XML shows a `<cookieHandler>` element.</span></span> <span data-ttu-id="e125a-165">在此範例中，因為 `mode` 未指定屬性，所以 SAM 會使用預設的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="e125a-165">In this example, because the `mode` attribute is not specified, the default cookie handler will be used by the SAM.</span></span> <span data-ttu-id="e125a-166">這是類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e125a-166">This is an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class.</span></span> <span data-ttu-id="e125a-167">由於 `<chunkedCookieHandler>` 未指定子項目，因此會使用預設的區塊大小。</span><span class="sxs-lookup"><span data-stu-id="e125a-167">Because the `<chunkedCookieHandler>` child element is not specified, the default chunk size will be used.</span></span> <span data-ttu-id="e125a-168">不需要 HTTPS，因為 `requireSsl` 已設定屬性 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e125a-168">HTTPS will not be required because the `requireSsl` attribute is set `false`.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="e125a-169">在此範例中，不需要 HTTPS 來寫入會話 cookie。</span><span class="sxs-lookup"><span data-stu-id="e125a-169">In this example, HTTPS is not required to write session cookies.</span></span> <span data-ttu-id="e125a-170">這是因為 `requireSsl` 元素上的屬性 `<cookieHandler>` 設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="e125a-170">This is because the `requireSsl` attribute on the `<cookieHandler>` element is set to `false`.</span></span> <span data-ttu-id="e125a-171">在大部分的生產環境中，不建議使用此設定，因為這可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="e125a-171">This setting is not recommended for most production environments as it may present a security risk.</span></span>  
  
```xml  
<cookieHandler requireSsl="false" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e125a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e125a-172">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
