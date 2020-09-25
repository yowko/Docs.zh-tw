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
ms.openlocfilehash: 8d792b967d967540469dca7c090e0f905ecb2e6b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201755"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="38013-102">webRequestModules 的 \<add> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="38013-102">\<add> Element for webRequestModules (Network Settings)</span></span>

<span data-ttu-id="38013-103">將自訂 Web 要求模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="38013-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="38013-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="38013-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38013-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38013-105">Attributes and Elements</span></span>  

 <span data-ttu-id="38013-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="38013-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38013-107">屬性</span><span class="sxs-lookup"><span data-stu-id="38013-107">Attributes</span></span>  
  
|<span data-ttu-id="38013-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="38013-108">**Attribute**</span></span>|<span data-ttu-id="38013-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="38013-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="38013-110">此 Web 要求模組所處理之要求的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="38013-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="38013-111">完整型別名稱 (由 <xref:System.Type.FullName%2A> 屬性) 指定，且由屬性) （以逗號分隔）所表示的元件名稱 (，以 <xref:System.Reflection.Assembly.FullName%2A> 執行此 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="38013-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38013-112">子元素</span><span class="sxs-lookup"><span data-stu-id="38013-112">Child Elements</span></span>  

 <span data-ttu-id="38013-113">無。</span><span class="sxs-lookup"><span data-stu-id="38013-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38013-114">父項目</span><span class="sxs-lookup"><span data-stu-id="38013-114">Parent Elements</span></span>  
  
|<span data-ttu-id="38013-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="38013-115">**Element**</span></span>|<span data-ttu-id="38013-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="38013-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="38013-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="38013-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="38013-118">指定用來向網路主機要求資訊的模組。</span><span class="sxs-lookup"><span data-stu-id="38013-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38013-119">備註</span><span class="sxs-lookup"><span data-stu-id="38013-119">Remarks</span></span>  

 <span data-ttu-id="38013-120">`prefix`屬性會定義使用指定 Web 要求模組的 URI 前置詞。</span><span class="sxs-lookup"><span data-stu-id="38013-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="38013-121">Web 要求模組通常會註冊來處理特定的通訊協定，例如 HTTP 或 FTP，但可以註冊來處理對伺服器上特定伺服器或路徑的要求。</span><span class="sxs-lookup"><span data-stu-id="38013-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="38013-122">當 URI 符合前置詞傳遞給方法時，就會建立 Web 要求模組 <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="38013-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="38013-123">屬性的值 `prefix` 應該是有效 URI 的開頭字元。</span><span class="sxs-lookup"><span data-stu-id="38013-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="38013-124">例如，`http` 或 `http://www.contoso.com`。</span><span class="sxs-lookup"><span data-stu-id="38013-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="38013-125">屬性的值 `type` 應為有效的型別名稱和對應的元件名稱，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="38013-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="38013-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="38013-126">Configuration Files</span></span>  

 <span data-ttu-id="38013-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="38013-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38013-128">範例</span><span class="sxs-lookup"><span data-stu-id="38013-128">Example</span></span>  

 <span data-ttu-id="38013-129">下列範例會註冊 HTTP 的自訂 Web 要求模組。</span><span class="sxs-lookup"><span data-stu-id="38013-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="38013-130">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="38013-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38013-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38013-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="38013-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="38013-132">Network Settings Schema</span></span>](index.md)
