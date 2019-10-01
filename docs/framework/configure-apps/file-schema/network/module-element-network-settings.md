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
ms.openlocfilehash: 15f4d10a70dc3c6abd32869f5b7b0006a799b4bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698036"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="38044-102">@no__t 0module > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="38044-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="38044-103">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="38044-103">Adds a new proxy module to the application.</span></span>  
  
[<span data-ttu-id="38044-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="38044-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="38044-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="38044-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="38044-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="38044-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="38044-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<module >**</span><span class="sxs-lookup"><span data-stu-id="38044-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38044-108">語法</span><span class="sxs-lookup"><span data-stu-id="38044-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38044-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38044-109">Attributes and Elements</span></span>  
 <span data-ttu-id="38044-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="38044-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38044-111">屬性</span><span class="sxs-lookup"><span data-stu-id="38044-111">Attributes</span></span>  
  
|<span data-ttu-id="38044-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="38044-112">**Attribute**</span></span>|<span data-ttu-id="38044-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="38044-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="38044-114">完整型別名稱（以 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（由 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示）（以逗號分隔），其會執行 proxy。</span><span class="sxs-lookup"><span data-stu-id="38044-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38044-115">子元素</span><span class="sxs-lookup"><span data-stu-id="38044-115">Child Elements</span></span>  
 <span data-ttu-id="38044-116">無。</span><span class="sxs-lookup"><span data-stu-id="38044-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38044-117">父項目</span><span class="sxs-lookup"><span data-stu-id="38044-117">Parent Elements</span></span>  
  
|<span data-ttu-id="38044-118">**目**</span><span class="sxs-lookup"><span data-stu-id="38044-118">**Element**</span></span>|<span data-ttu-id="38044-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="38044-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="38044-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="38044-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="38044-121">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="38044-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38044-122">備註</span><span class="sxs-lookup"><span data-stu-id="38044-122">Remarks</span></span>  
 <span data-ttu-id="38044-123">@No__t-0 元素會註冊用來執行 @no__t 1 介面的 proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="38044-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="38044-124">註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。</span><span class="sxs-lookup"><span data-stu-id="38044-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="38044-125">@No__t-0 屬性的值應該是模組的類別名稱，以及其對應動態連結程式庫（DLL）的名稱。</span><span class="sxs-lookup"><span data-stu-id="38044-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="38044-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="38044-126">Configuration Files</span></span>  
 <span data-ttu-id="38044-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="38044-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38044-128">範例</span><span class="sxs-lookup"><span data-stu-id="38044-128">Example</span></span>  
 <span data-ttu-id="38044-129">下列範例會註冊自訂 proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="38044-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38044-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38044-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="38044-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="38044-131">Network Settings Schema</span></span>](index.md)
