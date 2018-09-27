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
ms.openlocfilehash: 64df186be7d9e503ac22e177bca8da31e165f240
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47402665"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="d79bf-102">&lt;新增&gt;webRequestModules （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="d79bf-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="d79bf-103">將自訂的 Web 要求模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d79bf-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="d79bf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d79bf-104">\<configuration></span></span>  
<span data-ttu-id="d79bf-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d79bf-105">\<system.net></span></span>  
<span data-ttu-id="d79bf-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="d79bf-106">\<webRequestModules></span></span>  
<span data-ttu-id="d79bf-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d79bf-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d79bf-108">語法</span><span class="sxs-lookup"><span data-stu-id="d79bf-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d79bf-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d79bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d79bf-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d79bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d79bf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d79bf-111">Attributes</span></span>  
  
|<span data-ttu-id="d79bf-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d79bf-112">**Attribute**</span></span>|<span data-ttu-id="d79bf-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="d79bf-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="d79bf-114">此 Web 要求模組所處理的要求 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="d79bf-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="d79bf-115">完整的類型名稱 (由<xref:System.Type.FullName%2A>屬性) 和組件名稱 (由<xref:System.Reflection.Assembly.FullName%2A>屬性)，以實作此 Web 要求模組逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d79bf-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d79bf-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d79bf-116">Child Elements</span></span>  
 <span data-ttu-id="d79bf-117">無。</span><span class="sxs-lookup"><span data-stu-id="d79bf-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d79bf-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d79bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d79bf-119">**目**</span><span class="sxs-lookup"><span data-stu-id="d79bf-119">**Element**</span></span>|<span data-ttu-id="d79bf-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="d79bf-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d79bf-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d79bf-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="d79bf-122">指定要求資訊從網路主機使用的模組。</span><span class="sxs-lookup"><span data-stu-id="d79bf-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d79bf-123">備註</span><span class="sxs-lookup"><span data-stu-id="d79bf-123">Remarks</span></span>  
 <span data-ttu-id="d79bf-124">`prefix`屬性定義會使用指定的 Web 要求模組的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="d79bf-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="d79bf-125">Web 要求模組來處理特定的通訊協定，例如 HTTP 或 FTP，通常註冊，但可以向處理要求，以特定伺服器或伺服器上的路徑。</span><span class="sxs-lookup"><span data-stu-id="d79bf-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="d79bf-126">當符合 URI 的前置詞會傳遞至建立 Web 要求模組<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="d79bf-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d79bf-127">值`prefix`屬性應為有效的 URI 的前置字元。</span><span class="sxs-lookup"><span data-stu-id="d79bf-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="d79bf-128">例如，`http` 或 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="d79bf-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="d79bf-129">值`type`屬性應為有效的型別名稱和對應的組件名稱，以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d79bf-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="d79bf-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="d79bf-130">Configuration Files</span></span>  
 <span data-ttu-id="d79bf-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d79bf-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d79bf-132">範例</span><span class="sxs-lookup"><span data-stu-id="d79bf-132">Example</span></span>  
 <span data-ttu-id="d79bf-133">下列範例會註冊自訂的 Web 要求模組的 HTTP。</span><span class="sxs-lookup"><span data-stu-id="d79bf-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="d79bf-134">您應該取得版本和 PublicKeyToken 的值取代為正確的值，指定模組。</span><span class="sxs-lookup"><span data-stu-id="d79bf-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d79bf-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d79bf-135">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="d79bf-136">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d79bf-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
