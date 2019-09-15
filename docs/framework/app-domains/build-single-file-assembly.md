---
title: HOW TO：建立 .NET Framework 單一檔案元件
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98f06e62e1070f78faa77ef7d83fd80a62984684
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991239"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>HOW TO：建立 .NET Framework 單一檔案元件

單一檔案組件，是最簡單的組件類型，包含類型資訊和實作，以及[組件資訊清單](../../standard/assembly/manifest.md)。 您可以使用命令列編譯器或 Visual Studio 來建立以 .NET Framework 為目標的單一檔案元件。 根據預設，編譯器會建立副檔名為 *.exe*的元件檔。

> [!NOTE]
> Visual Studio for C# 和 Visual Basic 只能用於建立單一檔案組件。 如果想建立多檔案組件，您必須使用命令列編譯器或 Visual C++。

下列程序示範如何使用命令列編譯器建立單一檔案組件。

## <a name="create-an-assembly-with-an-exe-extension"></a>建立具有 .exe 副檔名的元件

在命令提示字元中輸入下列命令：

\<*編譯器命令*> \<*模組名稱*>

在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。

下列範例會從名`myCode`為的程式碼模組建立名為*myCode*的元件。

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>建立副檔名為 .exe 的元件，並指定輸出檔名稱

在命令提示字元中輸入下列命令：

\<*編譯器命令*>  **/out:** \<*檔案名稱*> \<*模組名稱*>

在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令、「檔案名稱」是輸出檔名稱，而「模組名稱」則是編譯至組件的程式碼模組名稱。

下列範例會從名`myCode`為的程式碼模組建立名為*myAssembly*的元件。

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>建立程式庫元件
 程式庫組件類似類別庫。 它包含其他組件會參考的類型，但沒有可開始執行的進入點。

若要建立程式庫元件，請在命令提示字元中輸入下列命令：

\<編譯器命令>  **-t:library** \<模組名稱>

在這個命令中，「編譯器命令」是您程式碼模組所用語言的編譯器命令，而「模組名稱」則是編譯至組件的程式碼模組名稱。 您也可以使用其他編譯器選項，例如 **out:** 選項。

下列範例會從名`myCode`為的程式碼模組建立名為 myCodeAssembly 的*連結*庫元件。

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>另請參閱

- [建立元件](../../standard/assembly/create.md)
- [多檔案元件](multifile-assemblies.md)
- [如何：建立多檔案元件](build-multifile-assembly.md)
- [具有元件的程式](../../standard/assembly/program.md)
