---
title: 指定組件的位置
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "81646024"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="31892-102">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="31892-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="31892-103">有兩種方式可以指定元件的位置：</span><span class="sxs-lookup"><span data-stu-id="31892-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="31892-104">使用 [\<codeBase>](./file-schema/runtime/codebase-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="31892-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="31892-105">使用 [\<probing>](./file-schema/runtime/probing-element.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="31892-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="31892-106">您也可以使用[.NET Framework 設定工具（mscorcfg.msc）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100))來指定元件位置，或指定 common language runtime 探查元件的位置。</span><span class="sxs-lookup"><span data-stu-id="31892-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="31892-107">使用 \<codeBase> 元素</span><span class="sxs-lookup"><span data-stu-id="31892-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="31892-108">您 **\<codeBase>** 只能在電腦設定或發行者原則檔（也就是也會重新導向元件版本）中使用元素。</span><span class="sxs-lookup"><span data-stu-id="31892-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="31892-109">當執行時間決定要使用的元件版本時，它會從判斷版本的檔案套用程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="31892-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="31892-110">如果沒有指定程式碼基底，執行時間會以正常方式探查元件。</span><span class="sxs-lookup"><span data-stu-id="31892-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="31892-111">如需詳細資訊，請參閱[執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="31892-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="31892-112">下列範例顯示如何指定元件的位置。</span><span class="sxs-lookup"><span data-stu-id="31892-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="31892-113">所有強式名稱元件都需要**version**屬性，但如果元件不是強式名稱，則應該予以省略。</span><span class="sxs-lookup"><span data-stu-id="31892-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="31892-114">**\<codeBase>** 元素需要**href**屬性。</span><span class="sxs-lookup"><span data-stu-id="31892-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="31892-115">您不能在元素中指定版本範圍 **\<codeBase>** 。</span><span class="sxs-lookup"><span data-stu-id="31892-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31892-116">如果您為不是以強式名稱命名的元件提供程式碼基底提示，則提示必須指向應用程式基底目錄或應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="31892-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="31892-117">使用 \<probing> 元素</span><span class="sxs-lookup"><span data-stu-id="31892-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="31892-118">執行時間會透過探查找出沒有程式碼基底的元件。</span><span class="sxs-lookup"><span data-stu-id="31892-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="31892-119">如需探查的詳細資訊，請參閱[執行時間如何找出元件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="31892-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="31892-120">您可以使用 [\<probing>](./file-schema/runtime/probing-element.md) 應用程式佈建檔中的專案，來指定執行時間在尋找元件時應搜尋的子目錄。</span><span class="sxs-lookup"><span data-stu-id="31892-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="31892-121">下列範例顯示如何指定執行時間應該搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="31892-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="31892-122">**PrivatePath**屬性包含執行時間應該搜尋元件的目錄。</span><span class="sxs-lookup"><span data-stu-id="31892-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="31892-123">如果應用程式位於 C:\Program Files\MyApp，則執行時間會尋找未在 C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin 和 C:\Program Files\MyApp\Bin3. 中指定程式碼基底的元件</span><span class="sxs-lookup"><span data-stu-id="31892-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="31892-124">**PrivatePath**中指定的目錄必須是應用程式基底目錄的子目錄。</span><span class="sxs-lookup"><span data-stu-id="31892-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31892-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31892-125">See also</span></span>

- [<span data-ttu-id="31892-126">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="31892-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="31892-127">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="31892-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="31892-128">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="31892-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="31892-129">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="31892-129">Configuring Apps by using Configuration Files</span></span>](index.md)
