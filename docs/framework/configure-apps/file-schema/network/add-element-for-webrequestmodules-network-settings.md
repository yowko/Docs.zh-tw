---
title: '&lt;新增&gt;webRequestModules （網路設定） 的項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 921f5f2bfda1a19d022d3f3f4131e3653fd17ea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742786"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="cdf81-102">&lt;新增&gt;webRequestModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="cdf81-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="cdf81-103">將自訂的 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="cdf81-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="cdf81-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="cdf81-104">\<configuration></span></span>  
<span data-ttu-id="cdf81-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cdf81-105">\<system.net></span></span>  
<span data-ttu-id="cdf81-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="cdf81-106">\<webRequestModules></span></span>  
<span data-ttu-id="cdf81-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cdf81-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf81-108">語法</span><span class="sxs-lookup"><span data-stu-id="cdf81-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf81-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cdf81-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cdf81-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cdf81-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdf81-111">屬性</span><span class="sxs-lookup"><span data-stu-id="cdf81-111">Attributes</span></span>  
  
|<span data-ttu-id="cdf81-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="cdf81-112">**Attribute**</span></span>|<span data-ttu-id="cdf81-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="cdf81-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="cdf81-114">此 Web 要求模組所處理的要求 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="cdf81-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="cdf81-115">完整限定的類型名稱 (由<xref:System.Type.FullName%2A>屬性) 和組件名稱 (由<xref:System.Reflection.Assembly.FullName%2A>屬性)、 分隔逗號，可實作此 Web 要求的模組。</span><span class="sxs-lookup"><span data-stu-id="cdf81-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdf81-116">子項目</span><span class="sxs-lookup"><span data-stu-id="cdf81-116">Child Elements</span></span>  
 <span data-ttu-id="cdf81-117">無。</span><span class="sxs-lookup"><span data-stu-id="cdf81-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdf81-118">父項目</span><span class="sxs-lookup"><span data-stu-id="cdf81-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cdf81-119">**目**</span><span class="sxs-lookup"><span data-stu-id="cdf81-119">**Element**</span></span>|<span data-ttu-id="cdf81-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="cdf81-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cdf81-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="cdf81-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="cdf81-122">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="cdf81-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf81-123">備註</span><span class="sxs-lookup"><span data-stu-id="cdf81-123">Remarks</span></span>  
 <span data-ttu-id="cdf81-124">`prefix`屬性定義會使用指定的 Web 要求模組的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="cdf81-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="cdf81-125">Web 要求模組來處理特定的通訊協定，例如 HTTP 或 FTP，通常註冊，但可以登錄來處理要求特定伺服器或伺服器上的路徑。</span><span class="sxs-lookup"><span data-stu-id="cdf81-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="cdf81-126">當符合 URI 的前置詞傳遞給建立 Web 要求模組<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="cdf81-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="cdf81-127">值`prefix`屬性應該是有效的 URI-例如，「 http 」 的前置字元或 "http://www.contoso.com" 。</span><span class="sxs-lookup"><span data-stu-id="cdf81-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="cdf81-128">值`type`屬性應為有效型別名稱和對應的組件名稱，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cdf81-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cdf81-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="cdf81-129">Configuration Files</span></span>  
 <span data-ttu-id="cdf81-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="cdf81-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf81-131">範例</span><span class="sxs-lookup"><span data-stu-id="cdf81-131">Example</span></span>  
 <span data-ttu-id="cdf81-132">下列範例會註冊自訂的 Web 要求模組的 HTTP。</span><span class="sxs-lookup"><span data-stu-id="cdf81-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="cdf81-133">您應該取得版本和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="cdf81-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdf81-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf81-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="cdf81-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="cdf81-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
