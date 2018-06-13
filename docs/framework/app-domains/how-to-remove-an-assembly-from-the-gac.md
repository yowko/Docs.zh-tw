---
title: 如何：從全域組件快取移除組件
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753725"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="5432e-102">如何：從全域組件快取移除組件</span><span class="sxs-lookup"><span data-stu-id="5432e-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="5432e-103">從全域組件快取 (GAC) 移除組件的方式有兩種：</span><span class="sxs-lookup"><span data-stu-id="5432e-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="5432e-104">使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="5432e-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="5432e-105">若要解除安裝開發和測試期間放在 GAC 中的組件，可使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="5432e-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="5432e-106">使用 [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5432e-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="5432e-107">若要解除安裝測試安裝套件時及針對生產系統所使用的組件，則應該使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="5432e-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="5432e-108">使用 Gacutil.exe 移除組件</span><span class="sxs-lookup"><span data-stu-id="5432e-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="5432e-109">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5432e-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="5432e-110">**gacutil –u** \<*組件名稱*></span><span class="sxs-lookup"><span data-stu-id="5432e-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="5432e-111">在這個命令中，「組件名稱」是要從全域組件快取移除的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5432e-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="5432e-112">您不應該使用 Gacutil.exe 移除生產系統上的組件，因為某個應用程式可能仍需要這個組件。</span><span class="sxs-lookup"><span data-stu-id="5432e-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="5432e-113">您應該改用 Windows Installer，以維護安裝在 GAC 中之每個組件的參考計數。</span><span class="sxs-lookup"><span data-stu-id="5432e-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="5432e-114">下列範例會從全域組件快取移除名為 `hello.dll` 的組件。</span><span class="sxs-lookup"><span data-stu-id="5432e-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="5432e-115">使用 Windows Installer 移除組件</span><span class="sxs-lookup"><span data-stu-id="5432e-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="5432e-116">從 [控制台] 中的 [程式和功能] 應用程式，選取您要解除安裝的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5432e-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="5432e-117">如果安裝套件將組件放在 GAC 中，Windows Installer 會在其他應用程式未使用這些組件時，將組件移除。</span><span class="sxs-lookup"><span data-stu-id="5432e-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5432e-118">Windows Installer 會維護安裝在 GAC 中之組件的參考計數。</span><span class="sxs-lookup"><span data-stu-id="5432e-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="5432e-119">只有在組件的參考計數到達零時 (表示 Windows Installer 套件所安裝的任何應用程式都未使用這個組件)，才能從 GAC 中移除組件。</span><span class="sxs-lookup"><span data-stu-id="5432e-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5432e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="5432e-120">See Also</span></span>  
 [<span data-ttu-id="5432e-121">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="5432e-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="5432e-122">操作說明：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="5432e-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="5432e-123">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="5432e-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
