---
title: 作法：檢視全域組件快取的內容
description: '瞭解如何使用全域組件快取 (GAC) 工具 ( # A0) ，在 .NET 中查看全域組件快取的內容。'
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
ms.openlocfilehash: 8b81f78f4ea28b3b9fca374029fe49f809826d8e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558559"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="621ff-103">操作說明：檢視全域組件快取的內容</span><span class="sxs-lookup"><span data-stu-id="621ff-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="621ff-104">您可以使用[全域組件快取工具 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取 (GAC) 的內容。</span><span class="sxs-lookup"><span data-stu-id="621ff-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="621ff-105">檢視 GAC 中的組件</span><span class="sxs-lookup"><span data-stu-id="621ff-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="621ff-106">若要檢視全域組件快取中的組件清單，請開啟 [Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md)，然後輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="621ff-106">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="621ff-107">-或-</span><span class="sxs-lookup"><span data-stu-id="621ff-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="621ff-108">在舊版 .NET Framework 中，[Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows Shell Extension 可讓您在 [檔案總管] 中檢視全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="621ff-108">In earlier versions of the .NET Framework, the [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="621ff-109">從 .NET Framework 4 開始，Shfusion.dll 已淘汰。</span><span class="sxs-lookup"><span data-stu-id="621ff-109">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="621ff-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="621ff-110">See also</span></span>

- [<span data-ttu-id="621ff-111">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="621ff-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="621ff-112">Gacutil.exe (全域組件快取工具) </span><span class="sxs-lookup"><span data-stu-id="621ff-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
