---
title: 如何：建置單一檔案組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aa39671da519ebf54dad52638ab940897209517
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-a-single-file-assembly"></a>如何：建置單一檔案組件
單一檔案組件，是最簡單的組件類型，包含類型資訊和實作，以及[組件資訊清單](../../../docs/framework/app-domains/assembly-manifest.md)。 您可以使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 來建立單一檔案組件。 編譯器預設會建立副檔名為 .exe 的組件檔案。  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C# 和 Visual Basic 只能用於建立單一檔案組件。 如想建立多檔案組件，您必須使用命令列編譯器或 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++。  
  
 下列程序示範如何使用命令列編譯器建立單一檔案組件。  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>建立副檔名為 .exe 的組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*編譯器命令*> \<*模組名稱*>  
  
     在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。  
  
 以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myCode.exe` 的組件。  
  
```console
csc myCode.cs  
```  

```console
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>建立副檔名為 .exe 的組件並指定輸出檔名稱  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<*編譯器命令*> **/out:**\<*檔案名稱*> \<*模組名稱*>  
  
     在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令、「檔案名稱」是輸出檔名稱，而「模組名稱」則是編譯至組件的程式碼模組名稱。  
  
 以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myAssembly.exe` 的組件。  
  
```console  
csc -out:myAssembly.exe myCode.cs  
```  
  
```console
vbc -out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>建立程式庫組件  
 程式庫組件類似類別庫。 它包含其他組件會參考的類型，但沒有可開始執行的進入點。  
  
#### <a name="to-create-a-library-assembly"></a>建立程式庫組件  
  
1.  在命令提示字元中輸入下列命令：  
  
     \<編譯器命令> **-t:library** \<模組名稱>  
  
     在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。 您也可以使用其他編譯器選項，例如 **out:** 選項。  
  
 以下範例會從稱為 `myCode` 的程式碼模組建立名為 `myCodeAssembly.dll` 的程式庫組件。  
  
```console  
csc -out:myCodeLibrary.dll -t:library myCode.cs  
```  
  
```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb  
```  
  
## <a name="see-also"></a>請參閱  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
 [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [操作說明：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
