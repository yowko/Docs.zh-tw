---
title: "如何：使用 DEVPATH 找出組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="47823-102">如何：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="47823-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="47823-103">開發人員可能想要確定他們建立的共用組件的多個應用程式正常運作。</span><span class="sxs-lookup"><span data-stu-id="47823-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="47823-104">而不是持續將組件在全域組件快取中，在開發期間，開發人員可以建立 DEVPATH 環境變數指向的組件的組建輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="47823-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="47823-105">例如，假設您正在建置呼叫 MySharedAssembly 共用組件並輸出目錄是 C:\MySharedAssembly\Debug。</span><span class="sxs-lookup"><span data-stu-id="47823-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="47823-106">您可以將 C:\MySharedAssembly\Debug DEVPATH 變數中。</span><span class="sxs-lookup"><span data-stu-id="47823-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="47823-107">您必須指定[ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)電腦組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="47823-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="47823-108">這個項目會告知 common language runtime 使用 DEVPATH 找出組件。</span><span class="sxs-lookup"><span data-stu-id="47823-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="47823-109">共用組件必須是由執行階段可探索。</span><span class="sxs-lookup"><span data-stu-id="47823-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="47823-110">若要指定私用來解析組件的參考使用目錄[\<程式碼基底 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)或[\<探查 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)在組態檔中所述[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="47823-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="47823-111">您也可以將組件放在應用程式目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="47823-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="47823-112">如需詳細資訊，請參閱 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="47823-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47823-113">這是一項進階的功能，僅供開發。</span><span class="sxs-lookup"><span data-stu-id="47823-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="47823-114">下列範例會示範如何使執行階段 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="47823-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47823-115">範例</span><span class="sxs-lookup"><span data-stu-id="47823-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="47823-116">這項設定會預設為 false。</span><span class="sxs-lookup"><span data-stu-id="47823-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47823-117">使用此設定只在開發階段。</span><span class="sxs-lookup"><span data-stu-id="47823-117">Use this setting only at development time.</span></span> <span data-ttu-id="47823-118">執行階段不會檢查 DEVPATH 中找到的強式名稱組件上的版本。</span><span class="sxs-lookup"><span data-stu-id="47823-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="47823-119">它只會使用第一個找到的組件。</span><span class="sxs-lookup"><span data-stu-id="47823-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47823-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47823-120">See Also</span></span>  
 [<span data-ttu-id="47823-121">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="47823-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
