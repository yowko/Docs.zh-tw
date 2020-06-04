---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397471"
---
# <a name="-netcf"></a>-netcf

設定編譯器以 .NET Compact Framework 為目標。

## <a name="syntax"></a>語法

```console
-netcf
```

## <a name="remarks"></a>備註

`-netcf`選項會導致 Visual Basic 編譯器以 .NET Compact Framework 為目標，而不是完整 .NET Framework。 只在完整 .NET Framework 中顯示的語言功能已停用。

`-netcf`選項是設計來搭配[-sdkpath](sdkpath.md)使用。 所停用的語言功能， `-netcf` 與以為目標的檔案中不存在相同的語言功能 `-sdkpath` 。

> [!NOTE]
> 此 `-netcf` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。 `-netcf`當載入 Visual Basic 裝置專案時，就會設定此選項。

`-netcf`選項會變更下列語言功能：

- 終止程式執行的[End \<keyword> 語句](../../language-reference/statements/end-keyword-statement.md)關鍵字已停用。 下列程式會編譯並執行， `-netcf` 但在編譯時期會失敗 `-netcf` 。

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- 所有形式的晚期繫結都會停用。 遇到可識別的晚期繫結案例時，就會產生編譯時期錯誤。 下列程式會編譯並執行， `-netcf` 但在編譯時期會失敗 `-netcf` 。

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../language-reference/modifiers/auto.md)、 [Ansi](../../language-reference/modifiers/ansi.md)和[Unicode](../../language-reference/modifiers/unicode.md)修飾詞已停用。 [Declare 語句](../../language-reference/statements/declare-statement.md)的語法也會修改為 `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` 。 下列程式碼會顯示 `-netcf` 編譯時的效果。

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- 使用從 Visual Basic 移除的 Visual Basic 6.0 關鍵字會在使用時產生不同的錯誤 `-netcf` 。 這會影響下列關鍵字的錯誤訊息：

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>範例

下列程式碼會 `Myfile.vb` 使用 .NET Compact Framework 進行編譯，其方式是在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到 mscorlib.dll 和 Microsoft 的版本。 一般來說，您會使用最新版本的 .NET Compact Framework。

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)
