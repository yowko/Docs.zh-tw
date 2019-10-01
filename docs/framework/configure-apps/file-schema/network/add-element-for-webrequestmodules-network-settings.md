---
title: webRequestModules 的 <add> 項目 (網路設定)
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
ms.openlocfilehash: 0248706ed78de160ef0131a0c7595374febf1aa9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699580"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="266d3-102">適用于 Webrequestmodules 專案的 @no__t 0add > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="266d3-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="266d3-103">將自訂 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="266d3-103">Adds a custom Web request module to the application.</span></span>  
  
[<span data-ttu-id="266d3-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="266d3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="266d3-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="266d3-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="266d3-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="266d3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="266d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="266d3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="266d3-108">語法</span><span class="sxs-lookup"><span data-stu-id="266d3-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="266d3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="266d3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="266d3-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="266d3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="266d3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="266d3-111">Attributes</span></span>  
  
|<span data-ttu-id="266d3-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="266d3-112">**Attribute**</span></span>|<span data-ttu-id="266d3-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="266d3-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="266d3-114">此 Web 要求模組所處理之要求的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="266d3-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="266d3-115">完整類型名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（由 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示）（以逗號分隔），其會執行此 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="266d3-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="266d3-116">子元素</span><span class="sxs-lookup"><span data-stu-id="266d3-116">Child Elements</span></span>  
 <span data-ttu-id="266d3-117">無。</span><span class="sxs-lookup"><span data-stu-id="266d3-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="266d3-118">父項目</span><span class="sxs-lookup"><span data-stu-id="266d3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="266d3-119">**目**</span><span class="sxs-lookup"><span data-stu-id="266d3-119">**Element**</span></span>|<span data-ttu-id="266d3-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="266d3-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="266d3-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="266d3-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="266d3-122">指定要用來要求網路主機資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="266d3-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="266d3-123">備註</span><span class="sxs-lookup"><span data-stu-id="266d3-123">Remarks</span></span>  
 <span data-ttu-id="266d3-124">@No__t-0 屬性會定義使用指定 Web 要求模組的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="266d3-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="266d3-125">Web 要求模組通常會註冊來處理特定的通訊協定（例如 HTTP 或 FTP），但是可以註冊以處理對伺服器上特定伺服器或路徑的要求。</span><span class="sxs-lookup"><span data-stu-id="266d3-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="266d3-126">當 URI 符合前置詞傳遞給 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 方法時，就會建立 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="266d3-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="266d3-127">@No__t-0 屬性的值應該是有效 URI 的前置字元。</span><span class="sxs-lookup"><span data-stu-id="266d3-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="266d3-128">例如，`http` 或 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="266d3-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="266d3-129">@No__t-0 屬性的值應該是有效的型別名稱和對應的元件名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="266d3-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="266d3-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="266d3-130">Configuration Files</span></span>  
 <span data-ttu-id="266d3-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="266d3-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="266d3-132">範例</span><span class="sxs-lookup"><span data-stu-id="266d3-132">Example</span></span>  
 <span data-ttu-id="266d3-133">下列範例會註冊 HTTP 的自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="266d3-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="266d3-134">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="266d3-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="266d3-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="266d3-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="266d3-136">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="266d3-136">Network Settings Schema</span></span>](index.md)
