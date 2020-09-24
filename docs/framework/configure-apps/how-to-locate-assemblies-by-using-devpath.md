---
title: 作法：使用 DEVPATH 找出組件
description: 使用 XML 電腦設定檔和 DEVPATH 環境變數，測試共用元件是否可在 .NET 中的許多應用程式中正確運作。
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 8ae807e46b11d2adb06d6af0c86e1c7297caa0c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161980"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="4f31a-103">作法：使用 DEVPATH 找出組件</span><span class="sxs-lookup"><span data-stu-id="4f31a-103">How to: Locate Assemblies by Using DEVPATH</span></span>

<span data-ttu-id="4f31a-104">開發人員可能會想要確保其所建立的共用元件能正確地搭配多個應用程式運作。</span><span class="sxs-lookup"><span data-stu-id="4f31a-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="4f31a-105">開發人員可以建立指向元件之組建輸出目錄的 DEVPATH 環境變數，而不是在開發週期期間持續將元件放在全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="4f31a-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="4f31a-106">例如，假設您正在建立名為 MySharedAssembly 的共用元件，而輸出目錄為 C:\MySharedAssembly\Debug。</span><span class="sxs-lookup"><span data-stu-id="4f31a-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="4f31a-107">您可以將 C:\MySharedAssembly\Debug 放在 DEVPATH 變數中。</span><span class="sxs-lookup"><span data-stu-id="4f31a-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="4f31a-108">然後，您必須 [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) 在電腦設定檔中指定元素。</span><span class="sxs-lookup"><span data-stu-id="4f31a-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="4f31a-109">這個元素會告知 common language runtime 使用 DEVPATH 來找出元件。</span><span class="sxs-lookup"><span data-stu-id="4f31a-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="4f31a-110">執行時間必須可探索共用的元件。</span><span class="sxs-lookup"><span data-stu-id="4f31a-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="4f31a-111">若要指定用來解析元件參考的私用目錄，請使用設定檔中的[ \<codeBase> 元素](./file-schema/runtime/codebase-element.md) [ \<probing> 或專案](./file-schema/runtime/probing-element.md)，如[指定元件的位置](specify-assembly-location.md)所述。</span><span class="sxs-lookup"><span data-stu-id="4f31a-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="4f31a-112">您也可以將元件放在應用程式目錄的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4f31a-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="4f31a-113">如需詳細資訊，請參閱 [執行階段如何找出組件](../deployment/how-the-runtime-locates-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="4f31a-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f31a-114">這是一項先進的功能，僅供開發之用。</span><span class="sxs-lookup"><span data-stu-id="4f31a-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="4f31a-115">下列範例示範如何使執行時間搜尋 DEVPATH 環境變數所指定之目錄中的元件。</span><span class="sxs-lookup"><span data-stu-id="4f31a-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f31a-116">範例</span><span class="sxs-lookup"><span data-stu-id="4f31a-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4f31a-117">此設定預設為 false。</span><span class="sxs-lookup"><span data-stu-id="4f31a-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f31a-118">請只在開發階段使用此設定。</span><span class="sxs-lookup"><span data-stu-id="4f31a-118">Use this setting only at development time.</span></span> <span data-ttu-id="4f31a-119">執行時間不會檢查在 DEVPATH 中找到之強式名稱元件的版本。</span><span class="sxs-lookup"><span data-stu-id="4f31a-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="4f31a-120">它只會使用它所找到的第一個元件。</span><span class="sxs-lookup"><span data-stu-id="4f31a-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f31a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f31a-121">See also</span></span>

- [<span data-ttu-id="4f31a-122">使用組態檔設定應用程式</span><span class="sxs-lookup"><span data-stu-id="4f31a-122">Configuring Apps by using Configuration Files</span></span>](index.md)
