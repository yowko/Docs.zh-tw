---
title: 將組件安裝到 GAC
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584577"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="ef927-102">操作說明：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="ef927-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="ef927-103">有兩種方式可以將強式名稱組件安裝到全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="ef927-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef927-104">只有強式名稱組件才能安裝至 GAC。</span><span class="sxs-lookup"><span data-stu-id="ef927-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="ef927-105">如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](how-to-sign-an-assembly-with-a-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="ef927-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="ef927-106">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="ef927-106">Windows Installer</span></span>

<span data-ttu-id="ef927-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。</span><span class="sxs-lookup"><span data-stu-id="ef927-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="ef927-108">Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。</span><span class="sxs-lookup"><span data-stu-id="ef927-108">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="ef927-109">您可以使用[適用於 Visual Studio 2017 的 WiX Toolset 擴充功能](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)，來建立 Windows Installer 的安裝程式套件。</span><span class="sxs-lookup"><span data-stu-id="ef927-109">You can use the [WiX Toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) to create an installer package for Windows Installer.</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="ef927-110">全域組件快取工具</span><span class="sxs-lookup"><span data-stu-id="ef927-110">Global assembly cache tool</span></span>

<span data-ttu-id="ef927-111">您可以使用[全域組件快取工具 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 將強式名稱的組件新增到全域組件快取，和檢視全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="ef927-111">You can use the [Global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ef927-112">Gacutil.exe 僅適合開發用途，不應用來安裝產品組件到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="ef927-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="ef927-113">gacutil 的語法如下：</span><span class="sxs-lookup"><span data-stu-id="ef927-113">The syntax for gacutil is as follows:</span></span>

```shell
gacutil -i <assembly name>
```

<span data-ttu-id="ef927-114">在這個命令中，「組件名稱」是安裝在全域組件快取的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="ef927-114">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="ef927-115">下列範例安裝檔名為 `hello.dll` 的組件到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="ef927-115">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>

```shell
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="ef927-116">在舊版 .NET Framework 中，可利用 Shfusion.dll Windows Shell Extension 將組件拖曳到 [檔案總管] 中，藉此安裝組件。</span><span class="sxs-lookup"><span data-stu-id="ef927-116">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in **File Explorer**.</span></span> <span data-ttu-id="ef927-117">從 .NET Framework 4 開始，Shfusion.dll 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="ef927-117">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef927-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef927-118">See also</span></span>

- [<span data-ttu-id="ef927-119">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="ef927-119">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="ef927-120">操作說明：從全域組件快取移除組件</span><span class="sxs-lookup"><span data-stu-id="ef927-120">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="ef927-121">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="ef927-121">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="ef927-122">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="ef927-122">How to: Sign an Assembly with a Strong Name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)