---
title: -nowin32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: d9323cd541eaf611551de90e58a181f6915fad89
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397450"
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="7fe91-102">-nowin32manifest （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7fe91-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="7fe91-103">指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="7fe91-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fe91-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fe91-104">Syntax</span></span>  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="7fe91-105">備註</span><span class="sxs-lookup"><span data-stu-id="7fe91-105">Remarks</span></span>  
 <span data-ttu-id="7fe91-106">使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。</span><span class="sxs-lookup"><span data-stu-id="7fe91-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="7fe91-107">如需虛擬化的詳細資訊，請參閱[Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。</span><span class="sxs-lookup"><span data-stu-id="7fe91-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="7fe91-108">如需建立資訊清單的詳細資訊，請參閱[-win32manifest （Visual Basic）](win32manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe91-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe91-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fe91-109">See also</span></span>

- [<span data-ttu-id="7fe91-110">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7fe91-110">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7fe91-111">Application Page, Project Designer (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fe91-111">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
