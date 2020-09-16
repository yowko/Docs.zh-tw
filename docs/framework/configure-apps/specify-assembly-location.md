---
title: 指定組件的位置
description: 請參閱如何使用程式碼基底元素或 XML 設定檔中的探查專案，在 .NET 中指定元件的位置。
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 3b24ff99eee9027d507ef89ca855162f221f826a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555116"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="1542d-103">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="1542d-103">Specifying an Assembly's Location</span></span>
<span data-ttu-id="1542d-104">有兩種方式可以指定元件的位置：</span><span class="sxs-lookup"><span data-stu-id="1542d-104">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="1542d-105">使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1542d-105">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="1542d-106">使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="1542d-106">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="1542d-107">您也可以使用 [.NET Framework 設定工具 (mscorcfg.msc) ](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) 指定元件位置，或指定 common language runtime 探查元件的位置。</span><span class="sxs-lookup"><span data-stu-id="1542d-107">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="1542d-108">使用 \<codeBase> 元素</span><span class="sxs-lookup"><span data-stu-id="1542d-108">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="1542d-109">您 **\<codeBase>** 只能在電腦設定或發行者原則檔中使用專案，也會重新導向元件版本。</span><span class="sxs-lookup"><span data-stu-id="1542d-109">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="1542d-110">當執行時間判斷要使用的元件版本時，會從決定版本的檔案套用程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="1542d-110">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="1542d-111">如果未指示任何程式碼基底，則執行時間會以一般方式探查元件。</span><span class="sxs-lookup"><span data-stu-id="1542d-111">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="1542d-112">如需詳細資訊，請參閱 [執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="1542d-112">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="1542d-113">下列範例顯示如何指定元件的位置。</span><span class="sxs-lookup"><span data-stu-id="1542d-113">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="1542d-114">所有強式名稱元件都必須要有 **version** 屬性，但是針對未強式名稱的元件，則應該省略。</span><span class="sxs-lookup"><span data-stu-id="1542d-114">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="1542d-115">**\<codeBase>** 元素需要**href**屬性。</span><span class="sxs-lookup"><span data-stu-id="1542d-115">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="1542d-116">您無法在元素中指定版本範圍 **\<codeBase>** 。</span><span class="sxs-lookup"><span data-stu-id="1542d-116">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1542d-117">如果您要為不是強式名稱的元件提供程式碼基底提示，則提示必須指向應用程式基底或應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="1542d-117">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="1542d-118">使用 \<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="1542d-118">Using the \<probing> Element</span></span>  
 <span data-ttu-id="1542d-119">執行時間會找出不具程式碼基底的元件（藉由探查）。</span><span class="sxs-lookup"><span data-stu-id="1542d-119">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="1542d-120">如需探查的詳細資訊，請參閱 [執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="1542d-120">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="1542d-121">您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 應用程式佈建檔中的專案，指定在尋找元件時，執行時間應搜尋的子目錄。</span><span class="sxs-lookup"><span data-stu-id="1542d-121">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="1542d-122">下列範例顯示如何指定執行時間應搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="1542d-122">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1542d-123">**PrivatePath**屬性包含執行時間應搜尋元件的目錄。</span><span class="sxs-lookup"><span data-stu-id="1542d-123">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="1542d-124">如果應用程式位於 C:\Program Files\MyApp，則執行時間會尋找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定程式碼基底的元件</span><span class="sxs-lookup"><span data-stu-id="1542d-124">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="1542d-125">**PrivatePath**中指定的目錄必須是應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="1542d-125">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1542d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1542d-126">See also</span></span>

- [<span data-ttu-id="1542d-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="1542d-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="1542d-128">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="1542d-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="1542d-129">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="1542d-129">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1542d-130">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="1542d-130">Configuring Apps by using Configuration Files</span></span>](index.md)
