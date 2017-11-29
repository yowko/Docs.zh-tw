---
title: /nowin32manifest (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce8e963e88a8080424435caea8b15ba288ae9c28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-visual-basic"></a><span data-ttu-id="9a829-102">/nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a829-102">/nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="9a829-103">指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="9a829-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a829-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a829-104">Syntax</span></span>  
  
```  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="9a829-105">備註</span><span class="sxs-lookup"><span data-stu-id="9a829-105">Remarks</span></span>  
 <span data-ttu-id="9a829-106">使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="9a829-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="9a829-107">如需虛擬化的詳細資訊，請參閱[ClickOnce 部署在 Windows Vista 上](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="9a829-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="9a829-108">如需建立資訊清單的詳細資訊，請參閱[/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="9a829-108">For more information about manifest creation, see [/win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a829-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a829-109">See Also</span></span>  
 [<span data-ttu-id="9a829-110">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="9a829-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9a829-111">專案設計工具、應用程式頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a829-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
