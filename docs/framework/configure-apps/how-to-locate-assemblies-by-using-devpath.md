---
title: 作法：使用 DEVPATH 找出組件
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "69912991"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="c313b-102">作法：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="c313b-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="c313b-103">開發人員可能會想要確定它們所建立的共用元件能與多個應用程式正確搭配運作。</span><span class="sxs-lookup"><span data-stu-id="c313b-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="c313b-104">開發人員可以建立 DEVPATH 環境變數，以指向元件的組建輸出目錄，而不是在開發週期期間持續將元件放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="c313b-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="c313b-105">例如，假設您要建立一個名為 MySharedAssembly 的共用元件，而輸出目錄是 C:\MySharedAssembly\Debug。</span><span class="sxs-lookup"><span data-stu-id="c313b-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="c313b-106">您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。</span><span class="sxs-lookup"><span data-stu-id="c313b-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="c313b-107">接著，您必須 [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) 在電腦設定檔中指定元素。</span><span class="sxs-lookup"><span data-stu-id="c313b-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="c313b-108">這個元素會告知 common language runtime 使用 DEVPATH 來尋找元件。</span><span class="sxs-lookup"><span data-stu-id="c313b-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="c313b-109">執行時間必須可探索共用元件。</span><span class="sxs-lookup"><span data-stu-id="c313b-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="c313b-110">若要指定解析元件參考的私用目錄，請使用設定檔中的[ \<codeBase> 元素](./file-schema/runtime/codebase-element.md)或[ \<probing> 元素](./file-schema/runtime/probing-element.md)，如[指定元件的位置](specify-assembly-location.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="c313b-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="c313b-111">您也可以將元件放在應用程式目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="c313b-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="c313b-112">如需詳細資訊，請參閱 [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="c313b-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c313b-113">這是一項先進的功能，僅供開發之用。</span><span class="sxs-lookup"><span data-stu-id="c313b-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="c313b-114">下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。</span><span class="sxs-lookup"><span data-stu-id="c313b-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c313b-115">範例</span><span class="sxs-lookup"><span data-stu-id="c313b-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="c313b-116">此設定的預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="c313b-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c313b-117">請只在開發階段使用此設定。</span><span class="sxs-lookup"><span data-stu-id="c313b-117">Use this setting only at development time.</span></span> <span data-ttu-id="c313b-118">執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。</span><span class="sxs-lookup"><span data-stu-id="c313b-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="c313b-119">它只會使用所找到的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="c313b-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c313b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c313b-120">See also</span></span>

- [<span data-ttu-id="c313b-121">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="c313b-121">Configuring Apps by using Configuration Files</span></span>](index.md)
