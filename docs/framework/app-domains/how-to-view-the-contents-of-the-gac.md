---
title: 作法：檢視全域組件快取的內容
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c319c5f7c9bb808b2ce7ee10178722287e456339
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486436"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="b7bef-102">作法：檢視全域組件快取的內容</span><span class="sxs-lookup"><span data-stu-id="b7bef-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="b7bef-103">您可以使用[全域組件快取工具 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取 (GAC) 的內容。</span><span class="sxs-lookup"><span data-stu-id="b7bef-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="b7bef-104">檢視 GAC 中的組件</span><span class="sxs-lookup"><span data-stu-id="b7bef-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="b7bef-105">若要檢視全域組件快取中的組件清單，請開啟 [Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md)，然後輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b7bef-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="b7bef-106">-或-</span><span class="sxs-lookup"><span data-stu-id="b7bef-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="b7bef-107">在舊版 .NET Framework 中，[Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows Shell Extension 可讓您在 [檔案總管] 中檢視全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="b7bef-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="b7bef-108">從 .NET Framework 4 開始，Shfusion.dll 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="b7bef-108">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7bef-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7bef-109">See also</span></span>

- [<span data-ttu-id="b7bef-110">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="b7bef-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="b7bef-111">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="b7bef-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
