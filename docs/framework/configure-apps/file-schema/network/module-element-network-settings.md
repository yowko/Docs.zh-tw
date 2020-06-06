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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154825"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="bca36-102">\<module> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="bca36-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="bca36-103">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="bca36-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="bca36-104">語法</span><span class="sxs-lookup"><span data-stu-id="bca36-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bca36-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bca36-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bca36-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bca36-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bca36-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bca36-107">Attributes</span></span>  
  
|<span data-ttu-id="bca36-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="bca36-108">**Attribute**</span></span>|<span data-ttu-id="bca36-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="bca36-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="bca36-110">完整型別名稱（由 <xref:System.Type.FullName%2A> 屬性工作表示）和元件名稱（由 <xref:System.Reflection.Assembly.FullName%2A> 屬性工作表示），並以逗號分隔，以執行 proxy。</span><span class="sxs-lookup"><span data-stu-id="bca36-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bca36-111">子元素</span><span class="sxs-lookup"><span data-stu-id="bca36-111">Child Elements</span></span>  
 <span data-ttu-id="bca36-112">無。</span><span class="sxs-lookup"><span data-stu-id="bca36-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bca36-113">父項目</span><span class="sxs-lookup"><span data-stu-id="bca36-113">Parent Elements</span></span>  
  
|<span data-ttu-id="bca36-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="bca36-114">**Element**</span></span>|<span data-ttu-id="bca36-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="bca36-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="bca36-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="bca36-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="bca36-117">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="bca36-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bca36-118">備註</span><span class="sxs-lookup"><span data-stu-id="bca36-118">Remarks</span></span>  
 <span data-ttu-id="bca36-119">`module`元素會註冊用來執行介面的 proxy 類別 <xref:System.Net.IWebProxy> 。</span><span class="sxs-lookup"><span data-stu-id="bca36-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="bca36-120">註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。</span><span class="sxs-lookup"><span data-stu-id="bca36-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="bca36-121">屬性的值 `type` 應該是模組的類別名稱，以及其對應動態連結程式庫（DLL）的名稱。</span><span class="sxs-lookup"><span data-stu-id="bca36-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="bca36-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="bca36-122">Configuration Files</span></span>  
 <span data-ttu-id="bca36-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="bca36-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca36-124">範例</span><span class="sxs-lookup"><span data-stu-id="bca36-124">Example</span></span>  
 <span data-ttu-id="bca36-125">下列範例會註冊自訂 proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="bca36-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bca36-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bca36-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="bca36-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bca36-127">Network Settings Schema</span></span>](index.md)
