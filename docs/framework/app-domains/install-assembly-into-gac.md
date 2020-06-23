---
title: 作法：將組件安裝到全域組件快取
description: 將元件安裝到 .NET 的全域組件快取（GAC）中，讓許多應用程式可以共用它。 使用 Windows Installer 或 GAC 公用程式。
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104670"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="89dcf-104">作法：將組件安裝到全域組件快取</span><span class="sxs-lookup"><span data-stu-id="89dcf-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="89dcf-105">全域組件快取 (GAC) 會儲存數個應用程式共用的組件。</span><span class="sxs-lookup"><span data-stu-id="89dcf-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="89dcf-106">使用下列其中一個元件，將組件安裝到[全域組件快取](gac.md)：</span><span class="sxs-lookup"><span data-stu-id="89dcf-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="89dcf-107">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="89dcf-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="89dcf-108">全域組件快取工具</span><span class="sxs-lookup"><span data-stu-id="89dcf-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="89dcf-109">您只能將強式名稱的元件安裝到全域組件快取中。</span><span class="sxs-lookup"><span data-stu-id="89dcf-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="89dcf-110">如需如何建立強式名稱元件的詳細資訊，請參閱[如何：使用強式名稱簽署元件](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="89dcf-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="89dcf-111">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="89dcf-111">Windows Installer</span></span>

<span data-ttu-id="89dcf-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。</span><span class="sxs-lookup"><span data-stu-id="89dcf-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="89dcf-113">Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。</span><span class="sxs-lookup"><span data-stu-id="89dcf-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="89dcf-114">若要建立 Windows Installer 的安裝程式套件，請使用[適用於 Visual Studio 2017 的 WiX Toolset 延伸模組](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。</span><span class="sxs-lookup"><span data-stu-id="89dcf-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="89dcf-115">全域組件快取工具</span><span class="sxs-lookup"><span data-stu-id="89dcf-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="89dcf-116">您可以使用[.Net 全域組件快取公用程式（gacutil.exe）](../tools/gacutil-exe-gac-tool.md)將元件加入至全域組件快取，以及查看全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="89dcf-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="89dcf-117">*Gacutil.exe* 只能用於開發目的。</span><span class="sxs-lookup"><span data-stu-id="89dcf-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="89dcf-118">請勿使用這個檔案將生產組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="89dcf-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="89dcf-119">使用 *gacutil.exe* 將組件安裝到 GAC 的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="89dcf-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="89dcf-120">在此命令中， *\<assembly name>* 是要在全域組件快取中安裝之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="89dcf-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="89dcf-121">如果*gacutil.exe*不在您的系統路徑中，請使用[VS *\<version>* 的開發人員命令提示](../tools/developer-command-prompt-for-vs.md)字元。</span><span class="sxs-lookup"><span data-stu-id="89dcf-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="89dcf-122">下列範例會將檔案名稱為 *hello.dll* 的組件安裝到全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="89dcf-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="89dcf-123">在舊版 .NET Framework 中，*Shfusion.dll* Windows 殼層延伸可讓您將組件拖曳到 [檔案總管]，藉此安裝組件。</span><span class="sxs-lookup"><span data-stu-id="89dcf-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="89dcf-124">從 .NET Framework 4 開始，*Shfusion.dll* 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="89dcf-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="89dcf-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89dcf-125">See also</span></span>

- [<span data-ttu-id="89dcf-126">使用元件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="89dcf-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="89dcf-127">如何：從全域組件快取移除元件</span><span class="sxs-lookup"><span data-stu-id="89dcf-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="89dcf-128">Gacutil.exe （全域組件快取工具）</span><span class="sxs-lookup"><span data-stu-id="89dcf-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="89dcf-129">如何：使用強式名稱簽署元件</span><span class="sxs-lookup"><span data-stu-id="89dcf-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
