---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28d0556a662099e4e5e74b22583fc3c8b4c313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-vbruntime"></a>-vbruntime
指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。  
  
## <a name="syntax"></a>語法  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>引數  
 \-  
 編譯 Visual Basic 執行階段程式庫參考。  
  
 \+  
 編譯預設 Visual Basic 執行階段程式庫的參考。  
  
 \*  
 編譯 Visual Basic 執行階段程式庫，必須參考和內嵌組件從 Visual Basic 執行階段程式庫的核心功能。  
  
 `path`  
 編譯指定的程式庫 (DLL) 的參考。  
  
## <a name="remarks"></a>備註  
 `-vbruntime`編譯器選項可讓您指定編譯器應編譯 Visual Basic 執行階段程式庫參考。 如果您沒有 Visual Basic 執行階段程式庫的參考編譯時，會在產生 Visual Basic 執行階段協助程式呼叫的程式碼或語言建構記錄錯誤或警告。 (A *Visual Basic 執行階段 helper*是定義在 Microsoft.VisualBasic.dll 中，在執行特定語言語意的執行階段呼叫的函式。)  
  
 `-vbruntime+`選項會產生相同的行為，如果沒有，就會發生`-vbruntime`指定參數。 您可以使用`-vbruntime+`選項來覆寫先前`-vbruntime`參數。  
  
 大部分物件`My`類型為無法使用，當您使用`-vbruntime-`或`-vbruntime:path`選項。  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>內嵌 Visual Basic 執行階段的核心功能  
 `-vbruntime*`選項可讓您編譯而不需要執行階段程式庫的參考。 相反地，從 Visual Basic 執行階段程式庫的核心功能會內嵌在使用者組件。 如果您的應用程式執行，並包含 Visual Basic 執行階段平台上，您可以使用此選項。  
  
 下列執行階段成員會內嵌：  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> 類別  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> 方法  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> 常數  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 常數  
  
-   某些物件`My`類型  
  
 如果您將編譯使用`-vbruntime*`選項和您的程式碼參考的成員，從非內嵌的核心功能與 Visual Basic 執行階段程式庫、 編譯器傳回錯誤，指出成員不是可用。  
  
## <a name="referencing-a-specified-library"></a>參考指定的程式庫  
 您可以使用`path`引數，若要編譯的自訂執行階段程式庫，而不使用預設 Visual Basic 執行階段程式庫的參考。  
  
 如果值`path`引數為 DLL 的完整的路徑，編譯器會使用該檔案做為執行階段程式庫。 如果值`path`引數不是 DLL 的完整的路徑，Visual Basic 編譯器會先搜尋目前資料夾中識別的 DLL。 它會在您使用指定的路徑中搜尋[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)編譯器選項。 如果`-sdkpath`未使用編譯器選項，編譯器會搜尋在.NET Framework 資料夾中識別的 DLL (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`-vbruntime`選項，以自訂的程式庫的參考所編譯。  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 核心 – Visual Studio 2010 SP1 中新的編譯模式](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
