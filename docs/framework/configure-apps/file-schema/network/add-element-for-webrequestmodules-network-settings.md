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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155020"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="ff62a-102">\<為 Web 請求模組添加>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="ff62a-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="ff62a-103">向應用程式添加自訂 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="ff62a-103">Adds a custom Web request module to the application.</span></span>  

<span data-ttu-id="ff62a-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ff62a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ff62a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ff62a-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="ff62a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<web 請求模組>**](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ff62a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="ff62a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="ff62a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ff62a-108">語法</span><span class="sxs-lookup"><span data-stu-id="ff62a-108">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff62a-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ff62a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ff62a-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="ff62a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff62a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ff62a-111">Attributes</span></span>  
  
|<span data-ttu-id="ff62a-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ff62a-112">**Attribute**</span></span>|<span data-ttu-id="ff62a-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="ff62a-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="ff62a-114">此 Web 請求模組處理的請求的 URI 首碼。</span><span class="sxs-lookup"><span data-stu-id="ff62a-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="ff62a-115">實現此 Web 請求模組的完全<xref:System.Type.FullName%2A>限定類型名稱（由屬性指示）和程式集<xref:System.Reflection.Assembly.FullName%2A>名稱（由屬性工作表示），由逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ff62a-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff62a-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ff62a-116">Child Elements</span></span>  
 <span data-ttu-id="ff62a-117">無。</span><span class="sxs-lookup"><span data-stu-id="ff62a-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff62a-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ff62a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ff62a-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="ff62a-119">**Element**</span></span>|<span data-ttu-id="ff62a-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="ff62a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ff62a-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="ff62a-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="ff62a-122">指定用於從網路主機請求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="ff62a-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff62a-123">備註</span><span class="sxs-lookup"><span data-stu-id="ff62a-123">Remarks</span></span>  
 <span data-ttu-id="ff62a-124">該`prefix`屬性定義使用指定的 Web 請求模組的 URI 首碼。</span><span class="sxs-lookup"><span data-stu-id="ff62a-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="ff62a-125">Web 請求模組通常註冊以處理特定協定（如 HTTP 或 FTP），但可以註冊以處理對伺服器上的特定伺服器或路徑的請求。</span><span class="sxs-lookup"><span data-stu-id="ff62a-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="ff62a-126">當 URI 匹配首碼傳遞給 方法時，<xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>將創建 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="ff62a-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ff62a-127">`prefix`屬性的值應為有效 URI 的前導字元。</span><span class="sxs-lookup"><span data-stu-id="ff62a-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="ff62a-128">例如，`http` 或 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="ff62a-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="ff62a-129">`type`屬性的值應是有效的類型名稱和相應的程式集名稱，用逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="ff62a-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="ff62a-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="ff62a-130">Configuration Files</span></span>  
 <span data-ttu-id="ff62a-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ff62a-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff62a-132">範例</span><span class="sxs-lookup"><span data-stu-id="ff62a-132">Example</span></span>  
 <span data-ttu-id="ff62a-133">以下示例註冊用於 HTTP 的自訂 Web 請求模組。</span><span class="sxs-lookup"><span data-stu-id="ff62a-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="ff62a-134">應將版本和 PublicKeyToken 的值替換為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="ff62a-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff62a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff62a-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="ff62a-136">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="ff62a-136">Network Settings Schema</span></span>](index.md)
