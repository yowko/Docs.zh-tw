---
title: 指定組件&#39;s 位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 65bd075115e33486e86e8081b01b96db665e9da5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="625a3-102">指定組件&#39;s 位置</span><span class="sxs-lookup"><span data-stu-id="625a3-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="625a3-103">有兩種方式來指定組件的位置：</span><span class="sxs-lookup"><span data-stu-id="625a3-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="625a3-104">使用[\<程式碼基底 >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="625a3-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="625a3-105">使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="625a3-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="625a3-106">您也可以使用[.NET Framework 組態工具 (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764)來指定組件的位置，或指定的 common language runtime 來探查組件位置。</span><span class="sxs-lookup"><span data-stu-id="625a3-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="625a3-107">使用\<程式碼基底 > 項目</span><span class="sxs-lookup"><span data-stu-id="625a3-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="625a3-108">您可以使用**\<程式碼基底 >** 只能在電腦組態檔或發行者原則檔，也會重新導向組件版本中的項目。</span><span class="sxs-lookup"><span data-stu-id="625a3-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="625a3-109">當執行階段會判定要使用的組件版本時，它會套用決定版本的檔案的程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="625a3-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="625a3-110">如果指示沒有程式碼基底，執行階段會以一般方式探查組件。</span><span class="sxs-lookup"><span data-stu-id="625a3-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="625a3-111">如需詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="625a3-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="625a3-112">下列範例會示範如何指定組件的位置。</span><span class="sxs-lookup"><span data-stu-id="625a3-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="625a3-113">**版本**屬性是必要的所有強式名稱組件，但應該省略不是強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="625a3-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="625a3-114">**\<程式碼基底 >** 元素需要**href**屬性。</span><span class="sxs-lookup"><span data-stu-id="625a3-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="625a3-115">您不能指定版本範圍中的**\<程式碼基底 >** 項目。</span><span class="sxs-lookup"><span data-stu-id="625a3-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="625a3-116">如果您不是強式名稱組件提供的程式碼基底的提示，此提示必須指向應用程式基底或應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="625a3-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="625a3-117">使用\<探查 > 項目</span><span class="sxs-lookup"><span data-stu-id="625a3-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="625a3-118">執行階段找出不需要程式碼基底探查的組件。</span><span class="sxs-lookup"><span data-stu-id="625a3-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="625a3-119">如需探查的詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="625a3-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="625a3-120">您可以使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)應用程式組態檔來指定執行階段尋找組件時，應該搜尋的子目錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="625a3-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="625a3-121">下列範例會示範如何指定執行階段應該搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="625a3-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="625a3-122">**Bin**屬性包含執行階段應該搜尋組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="625a3-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="625a3-123">如果應用程式位於 C:\Program Files\MyApp，執行階段會尋找 C:\Program Files\MyApp\Bin、 C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3 中未指定程式碼基底的組件。</span><span class="sxs-lookup"><span data-stu-id="625a3-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="625a3-124">指定之目錄**Bin**必須是應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="625a3-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625a3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="625a3-125">See Also</span></span>  
 [<span data-ttu-id="625a3-126">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="625a3-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="625a3-127">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="625a3-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="625a3-128">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="625a3-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="625a3-129">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="625a3-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
