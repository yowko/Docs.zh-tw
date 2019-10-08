---
title: -nowin32manifest （Visual Basic）
ms.date: 03/13/2018
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
ms.openlocfilehash: df05ff6caeae2fb2db6a8d7c8fec1b81774a9fa4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005384"
---
# <a name="-nowin32manifest-visual-basic"></a>-nowin32manifest （Visual Basic）
指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。  
  
## <a name="syntax"></a>語法  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>備註  
 使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。 如需虛擬化的詳細資訊，請參閱[Windows Vista 上的 ClickOnce 部署](/visualstudio/deployment/clickonce-deployment-on-windows-vista)。  
  
 如需建立資訊清單的詳細資訊，請參閱[-win32manifest （Visual Basic）](../../../visual-basic/reference/command-line-compiler/win32manifest.md)。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
