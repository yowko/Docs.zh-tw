---
title: 如何：建立 .NET Framework 單一檔案元件
description: 探索如何在 .NET 中建立單一檔案元件。 單一檔案元件可以是以 .NET 為目標的程式庫（.dll），也可以是可執行檔（.exe）。
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
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104924"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>如何：建立 .NET Framework 單一檔案元件

單一檔案組件，是最簡單的組件類型，包含類型資訊和實作，以及[組件資訊清單](../../standard/assembly/manifest.md)。 您可以使用命令列編譯器或 Visual Studio 來建立以 .NET Framework 為目標的單一檔案元件。 根據預設，編譯器會建立副檔名為 *.exe*的元件檔。

> [!NOTE]
> Visual Studio for C# 和 Visual Basic 只能用於建立單一檔案組件。 如果想建立多檔案組件，您必須使用命令列編譯器或 Visual C++。

下列程序示範如何使用命令列編譯器建立單一檔案組件。

## <a name="create-an-assembly-with-an-exe-extension"></a>建立具有 .exe 副檔名的元件

在命令提示字元中，輸入下列命令：

\<*compiler command*> \<*module name*>

在這個命令中，「編譯器命令」** 是您程式碼模組所用語言的編譯器命令，而「模組名稱」** 則是編譯至組件的程式碼模組名稱。

下列範例會從稱為的程式碼模組建立名為*myCode.exe*的元件 `myCode` 。

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>建立副檔名為 .exe 的元件，並指定輸出檔名稱

在命令提示字元中，輸入下列命令：

\<*compiler command*>**/out：** \<*file name*>\<*module name*>

在這個命令中，「編譯器命令」** 是您程式碼模組所用語言的編譯器命令、「檔案名稱」** 是輸出檔名稱，而「模組名稱」** 則是編譯至組件的程式碼模組名稱。

下列範例會從稱為的程式碼模組建立名為*myAssembly.exe*的元件 `myCode` 。

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>建立程式庫元件
 程式庫組件類似類別庫。 它包含其他組件會參考的類型，但沒有可開始執行的進入點。

若要建立程式庫元件，請在命令提示字元中輸入下列命令：

\<*compiler command*>**-t:library**\<*module name*>

在這個命令中，「編譯器命令」** 是您程式碼模組所用語言的編譯器命令，而「模組名稱」** 則是編譯至組件的程式碼模組名稱。 您也可以使用其他編譯器選項，例如 **out:** 選項。

下列範例會從稱為的程式碼模組建立名為*myCodeAssembly.dll*的程式庫元件 `myCode` 。

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>另請參閱

- [建立組件](../../standard/assembly/create.md)
- [多檔案組件](multifile-assemblies.md)
- [作法：建置多檔案組件](build-multifile-assembly.md)
- [具有組件的程式](../../standard/assembly/index.md)
