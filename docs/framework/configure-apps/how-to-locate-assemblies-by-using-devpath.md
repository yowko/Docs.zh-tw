---
title: HOW TO：使用 DEVPATH 找出組件
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 11ed84b01adf57eb526eaa1e71c6968e48c64cc2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627536"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="0bf29-102">HOW TO：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="0bf29-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="0bf29-103">開發人員可能想要確定自己進行建置，某個共用組件與多個應用程式正常運作。</span><span class="sxs-lookup"><span data-stu-id="0bf29-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="0bf29-104">而不是持續將組件在全域組件快取中放在開發期間，開發人員可以建立指向組件的組建輸出目錄 DEVPATH 環境變數。</span><span class="sxs-lookup"><span data-stu-id="0bf29-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="0bf29-105">例如，假設您正在建置呼叫 MySharedAssembly 某個共用組件，並輸出目錄是 C:\MySharedAssembly\Debug。</span><span class="sxs-lookup"><span data-stu-id="0bf29-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="0bf29-106">您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。</span><span class="sxs-lookup"><span data-stu-id="0bf29-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="0bf29-107">然後您必須指定[ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)電腦組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="0bf29-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="0bf29-108">這個項目會告知 common language runtime 使用 DEVPATH 找出組件。</span><span class="sxs-lookup"><span data-stu-id="0bf29-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="0bf29-109">共用的組件必須可由執行階段。</span><span class="sxs-lookup"><span data-stu-id="0bf29-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="0bf29-110">若要指定私用的目錄來解析組件的參考使用[\<程式碼基底 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)或是[\<探查 > 項目](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)在組態檔中所述[指定組件的位置](../../../docs/framework/configure-apps/specify-assembly-location.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf29-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="0bf29-111">您也可以將組件放在應用程式目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="0bf29-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="0bf29-112">如需詳細資訊，請參閱 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf29-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bf29-113">這是一項進階的功能，僅供開發。</span><span class="sxs-lookup"><span data-stu-id="0bf29-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="0bf29-114">下列範例示範如何讓執行階段搜尋 DEVPATH 環境變數所指定的目錄中的組件。</span><span class="sxs-lookup"><span data-stu-id="0bf29-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf29-115">範例</span><span class="sxs-lookup"><span data-stu-id="0bf29-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0bf29-116">此設定預設為 false。</span><span class="sxs-lookup"><span data-stu-id="0bf29-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bf29-117">使用此設定只在開發階段。</span><span class="sxs-lookup"><span data-stu-id="0bf29-117">Use this setting only at development time.</span></span> <span data-ttu-id="0bf29-118">執行階段不會檢查在 DEVPATH 中找到的強式名稱組件的版本。</span><span class="sxs-lookup"><span data-stu-id="0bf29-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="0bf29-119">它會直接使用第一個找到的組件。</span><span class="sxs-lookup"><span data-stu-id="0bf29-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf29-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bf29-120">See also</span></span>
- [<span data-ttu-id="0bf29-121">設定.NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="0bf29-121">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
