---
title: "如何：檢視全域組件快取的內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db5714c6669ac5fbdfd81656aa7659fdde05922a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="33fb0-102">如何：檢視全域組件快取的內容</span><span class="sxs-lookup"><span data-stu-id="33fb0-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="33fb0-103">您可以使用[全域組件快取工具 (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取的內容。</span><span class="sxs-lookup"><span data-stu-id="33fb0-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="33fb0-104">若要檢視全域組件快取中的組件清單</span><span class="sxs-lookup"><span data-stu-id="33fb0-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="33fb0-105">在 [Visual Studio 命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="33fb0-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="33fb0-106">**gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="33fb0-106">**gacutil -l** </span></span>  
     <span data-ttu-id="33fb0-107">-或-</span><span class="sxs-lookup"><span data-stu-id="33fb0-107">-or-</span></span>  
    <span data-ttu-id="33fb0-108">**gacutil /l**</span><span class="sxs-lookup"><span data-stu-id="33fb0-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="33fb0-109">在舊版 .NET Framework 中，[Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows Shell Extension 可讓您在 [檔案總管] 中檢視全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="33fb0-109">In earlier versions of the .NET Framework, the [Shfusion.dll](http://msdn.microsoft.com/en-us/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="33fb0-110">從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，Shfusion.dll 已過時。</span><span class="sxs-lookup"><span data-stu-id="33fb0-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33fb0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33fb0-111">See Also</span></span>  
 [<span data-ttu-id="33fb0-112">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="33fb0-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="33fb0-113">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="33fb0-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
