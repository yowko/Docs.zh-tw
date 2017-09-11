---
title: "/nowin32manifest (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 975711c9ee2e56b3c3c33611dd56eb6dc6082471
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="nowin32manifest-visual-basic"></a><span data-ttu-id="77ff1-102">/nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77ff1-102">/nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="77ff1-103">指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="77ff1-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ff1-104">語法</span><span class="sxs-lookup"><span data-stu-id="77ff1-104">Syntax</span></span>  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="77ff1-105">備註</span><span class="sxs-lookup"><span data-stu-id="77ff1-105">Remarks</span></span>  
 <span data-ttu-id="77ff1-106">使用此選項時，應用程式會受到 Windows Vista 上的虛擬化除非您提供的 Win32 資源檔案或更新版本的組建步驟期間的應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="77ff1-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="77ff1-107">如需虛擬化的詳細資訊，請參閱[Windows Vista 的 ClickOnce 部署](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="77ff1-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](https://docs.microsoft.com/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="77ff1-108">如需建立資訊清單的詳細資訊，請參閱[/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="77ff1-108">For more information about manifest creation, see [/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ff1-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77ff1-109">See Also</span></span>  
 <span data-ttu-id="77ff1-110">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="77ff1-110">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="77ff1-111"> [專案設計工具、應用程式頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="77ff1-111"> [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>
