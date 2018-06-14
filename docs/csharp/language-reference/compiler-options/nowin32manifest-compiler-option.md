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
ms.openlocfilehash: a07ead99ddd4e230fff8d1452ef81171ed849b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214928"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# 編譯器選項)
使用 **-nowin32manifest** 選項指示編譯器不要將任何應用程式資訊清單內嵌在可執行檔中。  
  
## <a name="syntax"></a>語法  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>備註  
 使用此選項時，應用程式在 Windows Vista 上會虛擬化，除非您在 Win32 資源檔案中或於更新版本組建步驟期間提供應用程式資訊清單。  
  
 在 Visual Studio 中，選取 [資訊清單] 下拉式清單的 [建立無資訊清單應用程式] 選項，在 [Application Property] (應用程式屬性) 頁面中設定這個選項。 如需詳細資訊，請參閱[專案設計工具、應用程式頁面 (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)。  
  
 如需建立資訊清單的詳細資訊，請參閱 [-win32manifest (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)。  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
