---
title: -nowin32manifest (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602709"
---
# <a name="-nowin32manifest-c-compiler-options"></a><span data-ttu-id="19d3c-102">-nowin32manifest (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="19d3c-102">-nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="19d3c-103">使用 **-nowin32manifest** 選項指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="19d3c-103">Use the **-nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d3c-104">語法</span><span class="sxs-lookup"><span data-stu-id="19d3c-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="19d3c-105">備註</span><span class="sxs-lookup"><span data-stu-id="19d3c-105">Remarks</span></span>  
 <span data-ttu-id="19d3c-106">使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="19d3c-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="19d3c-107">在 Visual Studio 中，選取 [資訊清單]  下拉式清單的 [建立無資訊清單應用程式]  選項，在 [Application Property] (應用程式屬性)  頁面中設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="19d3c-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="19d3c-108">如需詳細資訊，請參閱[專案設計工具、應用程式頁面 (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="19d3c-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="19d3c-109">如需建立資訊清單的詳細資訊，請參閱 [-win32manifest (C# 編譯器選項)](./win32manifest-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="19d3c-109">For more information about manifest creation, see [-win32manifest (C# Compiler Options)](./win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d3c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19d3c-110">See also</span></span>

- [<span data-ttu-id="19d3c-111">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="19d3c-111">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="19d3c-112">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="19d3c-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
