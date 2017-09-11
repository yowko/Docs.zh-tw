---
title: "-nowin32manifest (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowin32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: be52e05f962de636bd41d3c4df80a1ddfedb1eac
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="a99fe-102">/nowin32manifest (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="a99fe-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="a99fe-103">使用 [/nowin32manifest]**** 選項指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="a99fe-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a99fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="a99fe-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="a99fe-105">備註</span><span class="sxs-lookup"><span data-stu-id="a99fe-105">Remarks</span></span>  
 <span data-ttu-id="a99fe-106">使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a99fe-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="a99fe-107">在 Visual Studio 中，選取 [資訊清單]**** 下拉式清單的 [建立無資訊清單應用程式]**** 選項，在 [Application Property] (應用程式屬性)**** 頁面中設定這個選項。</span><span class="sxs-lookup"><span data-stu-id="a99fe-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="a99fe-108">如需詳細資訊，請參閱[專案設計工具、應用程式頁 (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="a99fe-108">For more information, see [Application Page, Project Designer (C#)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="a99fe-109">如需建立資訊清單的詳細資訊，請參閱[/win32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="a99fe-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99fe-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a99fe-110">See Also</span></span>  
 <span data-ttu-id="a99fe-111">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="a99fe-111">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="a99fe-112"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="a99fe-112"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
