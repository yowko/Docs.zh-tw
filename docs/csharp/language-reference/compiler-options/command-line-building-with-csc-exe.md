---
title: "使用 csc.exe 建置命令列"
ms.date: 04/19/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5fe7b735977b0cde0bed266815987b773be6bdbe
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="command-line-build-with-cscexe"></a>使用 csc.exe 建置命令列
您可以在命令提示字元中輸入 C# 編譯器的可執行檔名稱 (*csc.exe*)，藉此叫用該編譯器。

如果您使用 [Visual Studio 的開發人員命令提示字元] 視窗，所有必要的環境變數都會自動完成設定。 如需如何存取此工具的資訊，請參閱 [Visual Studio 的開發人員命令提示字元](../../../framework/tools/developer-command-prompt-for-vs.md)主題。 

如果您使用標準 [命令提示字元] 視窗，則必須先調整路徑，才能在電腦上的任何子目錄中叫用 *csc.exe*。 您也必須執行 *vsvars32.bat* 來設定適當的環境變數，以便支援命令列組建。 如需 *vsvars32.bat* 的詳細資訊，包括如何尋找和執行的指示，請參閱[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。

如果您是在只有 [!INCLUDE[winsdklong](~/includes/winsdklong-md.md)] 的電腦上工作，則可以在 [SDK 命令提示字元] (可從 [Microsoft .NET Framework SDK] 功能表選項開啟) 中使用 C# 編譯器。

您也可以使用 MSBuild 以程式設計的方式建置 C# 程式。 如需詳細資訊，請參閱 [MSBuild](/visualstudio/msbuild/msbuild)。

*csc.exe* 可執行檔通常位於 *Windows* 目錄下的 Microsoft.NET\Framework\\\<版本> 資料夾中。 它的位置可能依據特定電腦的實際組態而有所不同。 如果您的電腦上安裝了多個版本的 .NET Framework，您將看到這個檔案的多個版本。 如需這類安裝的詳細資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)。

> [!TIP]
>  當您使用 Visual Studio IDE 建置專案時，可以在 [輸出] 視窗中顯示 **csc** 命令和其關聯的編譯器選項。 若要顯示這項資訊，請遵循[如何：檢視、儲存和設定組建記錄檔](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log)中的指示，將記錄資料的詳細等級變更為 [一般] 或 [詳細]。 在您重新建置專案之後，請在 [輸出] 視窗中搜尋 **csc**，尋找 C# 編譯器的引動過程。

 **本主題內容**

- [命令列語法規則](#-rules-for-command-line-syntax-for-the-c-compiler)

- [範例命令列](#sample-command-lines-for-the-c-compiler)

- [C# 編譯器與 C++ 編譯器輸出的差異](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a>C# 編譯器命令列語法規則

C# 編譯器會在解譯作業系統命令列所指定的引數時使用下列規則：

- 引數會以空白或定位鍵的泛空白字元 (White Space) 進行分隔。

- 插入號字元 (^) 不會被辨識為逸出字元或分隔符號。 先由作業系統中的命令列剖析器處理字元，再將它傳遞給程式中的 `argv` 陣列。

- 不論其內是否包含空白字元，都會將以雙引號括住的字串 ("string") 解譯為單一引數。 有引號的字串可以內嵌到引數中。

- 前面有反斜線 (\\") 的雙引號會解譯為常值雙引號字元 (")。

- 反斜線會逐字解譯，除非後面緊接著雙引號。

- 如果雙引號後面加上偶數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，並將雙引號解譯為字串分隔符號。

- 如果雙引號後面加上奇數數目的反斜線，則會在每對反斜線的 `argv` 陣列中放入一個反斜線，並使用其餘的反斜線「逸出」雙引號。 這會在 `argv` 中新增常值雙引號 (")。

## <a name="sample-command-lines-for-the-c-compiler"></a>C# 編譯器命令列範例

- 編譯可產生 *File.exe* 的 *File.cs*：

```console
csc File.cs 
```

- 編譯可產生 *File.dll* 的 *File.cs*：

```console
csc -target:library File.cs
```

- 編譯 *File.cs* 並建立 *My.exe*：

```console
csc -out:My.exe File.cs
```

- 在啟用最佳化的情況下編譯目前目錄中的所有 C# 檔案，並定義 DEBUG 符號。 輸出為 *File2.exe*：

```console
csc -define:DEBUG -optimize -out:File2.exe *.cs
```

- 編譯產生 *File2.dll* 偵錯版本之目前目錄中的所有 C# 檔案。 不會顯示標誌和警告：

```console
csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
```

- 將目前目錄中的所有 C# 檔案都編譯為 *Something.xyz* (DLL)：

```console
csc -target:library -out:Something.xyz *.cs
```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a>C# 編譯器與 C++ 編譯器輸出的差異
叫用 C# 編譯器時並不會建立目的檔 (*.obj*)，而是直接建立輸出檔。 因此，C# 編譯器不需要連結器。

## <a name="see-also"></a>另請參閱
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 [依分類列出的 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [命令列引數](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
