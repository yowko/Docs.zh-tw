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
ms.openlocfilehash: ad641f93e93f627dae1c7d0bda4620093c4567b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205044"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="926d7-102">\<module> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="926d7-102">\<module> Element (Network Settings)</span></span>

<span data-ttu-id="926d7-103">將新的 Proxy 模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="926d7-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="926d7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="926d7-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="926d7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="926d7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="926d7-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="926d7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="926d7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="926d7-107">Attributes</span></span>  
  
|<span data-ttu-id="926d7-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="926d7-108">**Attribute**</span></span>|<span data-ttu-id="926d7-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="926d7-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="926d7-110">完整的型別名稱 (由 <xref:System.Type.FullName%2A> 屬性) 指出，以及由 <xref:System.Reflection.Assembly.FullName%2A> 屬性) （以逗號分隔，並以逗號分隔）所表示的元件名稱 (。</span><span class="sxs-lookup"><span data-stu-id="926d7-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="926d7-111">子元素</span><span class="sxs-lookup"><span data-stu-id="926d7-111">Child Elements</span></span>  

 <span data-ttu-id="926d7-112">無。</span><span class="sxs-lookup"><span data-stu-id="926d7-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="926d7-113">父項目</span><span class="sxs-lookup"><span data-stu-id="926d7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="926d7-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="926d7-114">**Element**</span></span>|<span data-ttu-id="926d7-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="926d7-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="926d7-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="926d7-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="926d7-117">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="926d7-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="926d7-118">備註</span><span class="sxs-lookup"><span data-stu-id="926d7-118">Remarks</span></span>  

 <span data-ttu-id="926d7-119">專案 `module` 會註冊執行介面的 proxy 類別 <xref:System.Net.IWebProxy> 。</span><span class="sxs-lookup"><span data-stu-id="926d7-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="926d7-120">註冊 Proxy 類別之後，可以使用 `module` 透過支援的 Proxy 要求資訊。</span><span class="sxs-lookup"><span data-stu-id="926d7-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="926d7-121">屬性的值 `type` 應該是模組的類別名稱，以及其對應的動態連結程式庫名稱， (DLL) 。</span><span class="sxs-lookup"><span data-stu-id="926d7-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="926d7-122">組態檔</span><span class="sxs-lookup"><span data-stu-id="926d7-122">Configuration Files</span></span>  

 <span data-ttu-id="926d7-123">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="926d7-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="926d7-124">範例</span><span class="sxs-lookup"><span data-stu-id="926d7-124">Example</span></span>  

 <span data-ttu-id="926d7-125">下列範例會註冊自訂 proxy 類別。</span><span class="sxs-lookup"><span data-stu-id="926d7-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="926d7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="926d7-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="926d7-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="926d7-127">Network Settings Schema</span></span>](index.md)
