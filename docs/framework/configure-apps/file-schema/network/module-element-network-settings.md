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
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084110"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="d5b30-102">\<模組 > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="d5b30-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="d5b30-103">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="d5b30-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="d5b30-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d5b30-104">\<configuration></span></span>  
<span data-ttu-id="d5b30-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d5b30-105">\<system.net></span></span>  
<span data-ttu-id="d5b30-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="d5b30-106">\<defaultProxy></span></span>  
<span data-ttu-id="d5b30-107">\<模組 ></span><span class="sxs-lookup"><span data-stu-id="d5b30-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b30-108">語法</span><span class="sxs-lookup"><span data-stu-id="d5b30-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5b30-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5b30-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d5b30-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d5b30-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5b30-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d5b30-111">Attributes</span></span>  
  
|<span data-ttu-id="d5b30-112">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d5b30-112">**Attribute**</span></span>|<span data-ttu-id="d5b30-113">**描述**</span><span class="sxs-lookup"><span data-stu-id="d5b30-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="d5b30-114">完整的類型名稱 (由<xref:System.Type.FullName%2A>屬性) 和組件名稱 (由<xref:System.Reflection.Assembly.FullName%2A>屬性)，以實作 proxy 逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="d5b30-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5b30-115">子元素</span><span class="sxs-lookup"><span data-stu-id="d5b30-115">Child Elements</span></span>  
 <span data-ttu-id="d5b30-116">無。</span><span class="sxs-lookup"><span data-stu-id="d5b30-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d5b30-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d5b30-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d5b30-118">**目**</span><span class="sxs-lookup"><span data-stu-id="d5b30-118">**Element**</span></span>|<span data-ttu-id="d5b30-119">**描述**</span><span class="sxs-lookup"><span data-stu-id="d5b30-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d5b30-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="d5b30-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="d5b30-121">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d5b30-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5b30-122">備註</span><span class="sxs-lookup"><span data-stu-id="d5b30-122">Remarks</span></span>  
 <span data-ttu-id="d5b30-123">`module`項目會註冊 proxy 類別可實作<xref:System.Net.IWebProxy>介面。</span><span class="sxs-lookup"><span data-stu-id="d5b30-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="d5b30-124">註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。</span><span class="sxs-lookup"><span data-stu-id="d5b30-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="d5b30-125">值`type`屬性應該是類別名稱的模組和名稱的其對應動態連結程式庫 (DLL)。</span><span class="sxs-lookup"><span data-stu-id="d5b30-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d5b30-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="d5b30-126">Configuration Files</span></span>  
 <span data-ttu-id="d5b30-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d5b30-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b30-128">範例</span><span class="sxs-lookup"><span data-stu-id="d5b30-128">Example</span></span>  
 <span data-ttu-id="d5b30-129">下列範例會註冊自訂的 proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="d5b30-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5b30-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5b30-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="d5b30-131">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d5b30-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
