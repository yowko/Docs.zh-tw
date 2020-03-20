---
title: <module> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154825"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="e2763-102">\<模組>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="e2763-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="e2763-103">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="e2763-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="e2763-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2763-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2763-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e2763-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e2763-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e2763-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="e2763-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<模組>**</span><span class="sxs-lookup"><span data-stu-id="e2763-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e2763-108">語法</span><span class="sxs-lookup"><span data-stu-id="e2763-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2763-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2763-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2763-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2763-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2763-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e2763-111">Attributes</span></span>  
  
|<span data-ttu-id="e2763-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="e2763-112">**Attribute**</span></span>|<span data-ttu-id="e2763-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="e2763-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="e2763-114">完全限定的類型名稱（由<xref:System.Type.FullName%2A>屬性指示）和程式集名稱（由<xref:System.Reflection.Assembly.FullName%2A>屬性工作表示），由逗號分隔，實現代理。</span><span class="sxs-lookup"><span data-stu-id="e2763-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2763-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e2763-115">Child Elements</span></span>  
 <span data-ttu-id="e2763-116">無。</span><span class="sxs-lookup"><span data-stu-id="e2763-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2763-117">父項目</span><span class="sxs-lookup"><span data-stu-id="e2763-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e2763-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e2763-118">**Element**</span></span>|<span data-ttu-id="e2763-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="e2763-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e2763-120">預設代理</span><span class="sxs-lookup"><span data-stu-id="e2763-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="e2763-121">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="e2763-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2763-122">備註</span><span class="sxs-lookup"><span data-stu-id="e2763-122">Remarks</span></span>  
 <span data-ttu-id="e2763-123">元素`module`註冊實現介面的<xref:System.Net.IWebProxy>代理類。</span><span class="sxs-lookup"><span data-stu-id="e2763-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="e2763-124">註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。</span><span class="sxs-lookup"><span data-stu-id="e2763-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="e2763-125">`type`屬性的值應是模組的類名及其相應的動態連結程式庫 （DLL） 的名稱。</span><span class="sxs-lookup"><span data-stu-id="e2763-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e2763-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="e2763-126">Configuration Files</span></span>  
 <span data-ttu-id="e2763-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="e2763-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2763-128">範例</span><span class="sxs-lookup"><span data-stu-id="e2763-128">Example</span></span>  
 <span data-ttu-id="e2763-129">下面的示例註冊自訂代理類。</span><span class="sxs-lookup"><span data-stu-id="e2763-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2763-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2763-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e2763-131">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="e2763-131">Network Settings Schema</span></span>](index.md)
