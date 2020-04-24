---
title: 指定組件的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646024"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="29c96-102">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="29c96-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="29c96-103">有兩種方法可以指定程式集的位置:</span><span class="sxs-lookup"><span data-stu-id="29c96-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="29c96-104">使用[\<代碼庫>](./file-schema/runtime/codebase-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="29c96-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="29c96-105">使用[\<探測>](./file-schema/runtime/probing-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="29c96-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="29c96-106">您還可以使用[.NET 框架設定工具 (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))指定程式集位置或指定要探測程式集的通用語言執行時的位置。</span><span class="sxs-lookup"><span data-stu-id="29c96-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="29c96-107">使用\<程式庫>元素</span><span class="sxs-lookup"><span data-stu-id="29c96-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="29c96-108">只能在電腦配置或發佈者策略檔中使用**\<codeBase>** 元素,這些檔也會重定向程式集版本。</span><span class="sxs-lookup"><span data-stu-id="29c96-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="29c96-109">當運行時確定要使用的程式集版本時,它將從確定版本的檔中應用代碼庫設置。</span><span class="sxs-lookup"><span data-stu-id="29c96-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="29c96-110">如果未指示代碼庫,則以正常方式探測程式集的運行時探測。</span><span class="sxs-lookup"><span data-stu-id="29c96-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="29c96-111">有關詳細資訊,請參閱[執行時如何尋找程式集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="29c96-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="29c96-112">下面的範例示範如何指定程式集的位置。</span><span class="sxs-lookup"><span data-stu-id="29c96-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="29c96-113">所有強命名程式集都需要**版本**屬性,但對於未強命名的程式集,應省略版本屬性。</span><span class="sxs-lookup"><span data-stu-id="29c96-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="29c96-114">代碼庫>元素需要**href**屬性。 \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="29c96-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="29c96-115">不能在**\<代碼庫>** 元素中指定版本範圍。</span><span class="sxs-lookup"><span data-stu-id="29c96-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29c96-116">如果要為未強命名的程式集提供代碼基提示,則提示必須指向應用程式基或應用程式基目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="29c96-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="29c96-117">使用\<探測>元素</span><span class="sxs-lookup"><span data-stu-id="29c96-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="29c96-118">運行時通過探測查找沒有代碼庫的程式集。</span><span class="sxs-lookup"><span data-stu-id="29c96-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="29c96-119">有關偵測的詳細資訊,請參閱[執行時如何查找程式集](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="29c96-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="29c96-120">可以使用應用程式設定檔中的[\<探測>](./file-schema/runtime/probing-element.md)元素來指定運行時在定位程式集時應搜索的子目錄。</span><span class="sxs-lookup"><span data-stu-id="29c96-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="29c96-121">下面的範例展示如何指定運行時應搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="29c96-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="29c96-122">**專用 Path**屬性包含運行時應搜索程式集的目錄。</span><span class="sxs-lookup"><span data-stu-id="29c96-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="29c96-123">如果應用程式位於 C:_程式檔\MyApp,執行時將查找未在 C:\*程式檔_MyApp_Bin、C:程式檔\MyApp_Subbin和 C:程式檔\MyApp_Bin3中指定代碼庫的程式集。</span><span class="sxs-lookup"><span data-stu-id="29c96-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="29c96-124">**在私有路徑**中指定的目錄必須是應用程式基礎目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="29c96-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c96-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29c96-125">See also</span></span>

- [<span data-ttu-id="29c96-126">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="29c96-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="29c96-127">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="29c96-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="29c96-128">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="29c96-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="29c96-129">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="29c96-129">Configuring Apps by using Configuration Files</span></span>](index.md)
