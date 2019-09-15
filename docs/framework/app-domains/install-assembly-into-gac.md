---
title: 作法：將組件安裝到全域組件快取
ms.date: 08/20/2019
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
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972932"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="de7bd-102">作法：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="de7bd-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="de7bd-103">全域組件快取 (GAC) 會儲存數個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="de7bd-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="de7bd-104">使用下列其中一個元件，將組件安裝到[全域組件快取](gac.md)：</span><span class="sxs-lookup"><span data-stu-id="de7bd-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="de7bd-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="de7bd-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="de7bd-106">全域組件快取工具</span><span class="sxs-lookup"><span data-stu-id="de7bd-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="de7bd-107">您只能將強式名稱的元件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="de7bd-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="de7bd-108">如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="de7bd-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="de7bd-109">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="de7bd-109">Windows Installer</span></span>

<span data-ttu-id="de7bd-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。</span><span class="sxs-lookup"><span data-stu-id="de7bd-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="de7bd-111">Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。</span><span class="sxs-lookup"><span data-stu-id="de7bd-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="de7bd-112">若要建立 Windows Installer 的安裝程式套件，請使用[適用於 Visual Studio 2017 的 WiX Toolset 延伸模組](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。</span><span class="sxs-lookup"><span data-stu-id="de7bd-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="de7bd-113">全域組件快取工具</span><span class="sxs-lookup"><span data-stu-id="de7bd-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="de7bd-114">您可以使用[.Net 全域組件快取公用程式（gacutil）](../tools/gacutil-exe-gac-tool.md)將元件加入至全域組件快取，以及查看全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="de7bd-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="de7bd-115">*Gacutil.exe* 只能用於開發目的。</span><span class="sxs-lookup"><span data-stu-id="de7bd-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="de7bd-116">請勿使用這個檔案將生產組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="de7bd-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="de7bd-117">使用 *gacutil.exe* 將組件安裝到 GAC 的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="de7bd-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="de7bd-118">在這個命令中，\<組件名稱> 是安裝在全域組件快取的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="de7bd-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="de7bd-119">如果*gacutil*不在您的系統路徑中，請使用[適用于 VS  *\<版本*的開發人員命令提示字元 >](../tools/developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="de7bd-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="de7bd-120">下列範例會將檔案名稱為 *hello.dll* 的組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="de7bd-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="de7bd-121">在舊版 .NET Framework 中，*Shfusion.dll* Windows 殼層延伸可讓您將組件拖曳到 [檔案總管]，藉此安裝組件。</span><span class="sxs-lookup"><span data-stu-id="de7bd-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="de7bd-122">從 .NET Framework 4 開始，*Shfusion.dll* 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="de7bd-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="de7bd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de7bd-123">See also</span></span>

- [<span data-ttu-id="de7bd-124">使用元件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="de7bd-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="de7bd-125">如何：從全域組件快取移除組件</span><span class="sxs-lookup"><span data-stu-id="de7bd-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="de7bd-126">Gacutil （全域組件快取工具）</span><span class="sxs-lookup"><span data-stu-id="de7bd-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="de7bd-127">如何：使用強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="de7bd-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
