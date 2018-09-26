---
title: 指定組件&#39;位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8fedec60b6152e77d6f99bf55cf11ec909fa8f80
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203978"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="51f51-102">指定組件&#39;位置</span><span class="sxs-lookup"><span data-stu-id="51f51-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="51f51-103">有兩種方式可指定組件的位置：</span><span class="sxs-lookup"><span data-stu-id="51f51-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="51f51-104">使用[\<程式碼基底 >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="51f51-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="51f51-105">使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="51f51-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="51f51-106">您也可以使用[.NET Framework 組態工具 (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764)來指定組件的位置，或指定通用語言執行平台，來探查組件的位置。</span><span class="sxs-lookup"><span data-stu-id="51f51-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="51f51-107">使用\<程式碼基底 > 項目</span><span class="sxs-lookup"><span data-stu-id="51f51-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="51f51-108">您可以使用**\<程式碼基底 >** 只能在機器組態或發行者原則檔案，也將重新導向組件版本中的項目。</span><span class="sxs-lookup"><span data-stu-id="51f51-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="51f51-109">當執行階段判斷要使用的組件版本時，它適用於決定版本檔案的程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="51f51-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="51f51-110">如果沒有程式碼基底指示，執行階段會以一般方式探查組件。</span><span class="sxs-lookup"><span data-stu-id="51f51-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="51f51-111">如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="51f51-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="51f51-112">下列範例示範如何指定組件的位置。</span><span class="sxs-lookup"><span data-stu-id="51f51-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="51f51-113">**版本**屬性所需的所有強式名稱組件，但應該不是強式名稱的組件中省略。</span><span class="sxs-lookup"><span data-stu-id="51f51-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="51f51-114">**\<程式碼基底 >** 項目需要**href**屬性。</span><span class="sxs-lookup"><span data-stu-id="51f51-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="51f51-115">您不能指定版本範圍**\<程式碼基底 >** 項目。</span><span class="sxs-lookup"><span data-stu-id="51f51-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51f51-116">如果您不是強式名稱組件提供的程式碼基底的提示，此提示必須指向應用程式基底或應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="51f51-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="51f51-117">使用\<探查 > 項目</span><span class="sxs-lookup"><span data-stu-id="51f51-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="51f51-118">執行階段找出並沒有程式碼基底所探查的組件。</span><span class="sxs-lookup"><span data-stu-id="51f51-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="51f51-119">如需有關探查的詳細資訊，請參閱[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="51f51-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="51f51-120">您可以使用[\<探查 >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)應用程式組態檔來指定執行階段尋找組件時，應該搜尋的子目錄中的項目。</span><span class="sxs-lookup"><span data-stu-id="51f51-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="51f51-121">下列範例示範如何指定執行階段應該搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="51f51-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="51f51-122">**Bin**屬性包含執行階段應該搜尋組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="51f51-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="51f51-123">如果應用程式位於 C:\Program Files\MyApp，執行階段會尋找組件不會在 C:\Program Files\MyApp\Bin、 C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3 中指定的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="51f51-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="51f51-124">中指定的目錄**Bin**必須是應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="51f51-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f51-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f51-125">See Also</span></span>  
 [<span data-ttu-id="51f51-126">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="51f51-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="51f51-127">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="51f51-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="51f51-128">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="51f51-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="51f51-129">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="51f51-129">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
