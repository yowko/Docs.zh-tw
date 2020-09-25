---
title: <probing> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: 1435ee8ea887b5d7d3e785eef0f25ffed14b1b97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195268"
---
# <a name="probing-element"></a><span data-ttu-id="77c2c-102">\<probing> 項目</span><span class="sxs-lookup"><span data-stu-id="77c2c-102">\<probing> Element</span></span>

<span data-ttu-id="77c2c-103">指定載入元件時，common language runtime 要搜尋的應用程式基底子目錄。</span><span class="sxs-lookup"><span data-stu-id="77c2c-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="77c2c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="77c2c-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77c2c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="77c2c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="77c2c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="77c2c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77c2c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="77c2c-107">Attributes</span></span>  
  
|<span data-ttu-id="77c2c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="77c2c-108">Attribute</span></span>|<span data-ttu-id="77c2c-109">描述</span><span class="sxs-lookup"><span data-stu-id="77c2c-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="77c2c-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="77c2c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="77c2c-111">指定可能包含元件之應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="77c2c-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="77c2c-112">使用分號分隔每個子目錄。</span><span class="sxs-lookup"><span data-stu-id="77c2c-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77c2c-113">子元素</span><span class="sxs-lookup"><span data-stu-id="77c2c-113">Child Elements</span></span>  

<span data-ttu-id="77c2c-114">無。</span><span class="sxs-lookup"><span data-stu-id="77c2c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77c2c-115">父項目</span><span class="sxs-lookup"><span data-stu-id="77c2c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="77c2c-116">項目</span><span class="sxs-lookup"><span data-stu-id="77c2c-116">Element</span></span>|<span data-ttu-id="77c2c-117">描述</span><span class="sxs-lookup"><span data-stu-id="77c2c-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="77c2c-118">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="77c2c-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="77c2c-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="77c2c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="77c2c-120">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="77c2c-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77c2c-121">範例</span><span class="sxs-lookup"><span data-stu-id="77c2c-121">Example</span></span>  

 <span data-ttu-id="77c2c-122">下列範例顯示如何指定執行時間應該搜尋元件的應用程式基底子目錄。</span><span class="sxs-lookup"><span data-stu-id="77c2c-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77c2c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77c2c-123">See also</span></span>

- [<span data-ttu-id="77c2c-124">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="77c2c-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="77c2c-125">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="77c2c-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="77c2c-126">指定元件的位置</span><span class="sxs-lookup"><span data-stu-id="77c2c-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="77c2c-127">執行時間如何找出元件</span><span class="sxs-lookup"><span data-stu-id="77c2c-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
