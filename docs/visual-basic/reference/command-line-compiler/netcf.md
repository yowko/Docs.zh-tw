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
ms.openlocfilehash: 028fa148d0e5622648a5fdfff1789c3d0bfde057
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268277"
---
# <a name="-netcf"></a>-netcf

設定.NET Compact Framework 為目標的編譯器。

## <a name="syntax"></a>語法

```
-netcf
```

## <a name="remarks"></a>備註

`-netcf`選項可讓以.NET Compact Framework，而不是完整的.NET Framework 為目標的 Visual Basic 編譯器。 是完整的.NET Framework 中的語言功能已停用。

`-netcf`選項設計來搭配[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)。 停用的語言功能`-netcf`都是相同的語言功能不存在於目標檔案`-sdkpath`。

> [!NOTE]
> `-netcf`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。 `-netcf` Visual Basic 裝置專案載入時，設定選項。

`-netcf`選項會變更下列語言功能：

- [結束\<關鍵字 > 陳述式](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字，結束執行程式，已停用。 下列程式會編譯並執行時不會`-netcf`會在編譯階段失敗，但`-netcf`。

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- 晚期繫結時，在所有表單中，已停用。 遇到已辨識的晚期繫結情節時，會產生編譯時期錯誤。 下列程式會編譯並執行時不會`-netcf`會在編譯階段失敗，但`-netcf`。

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [自動](../../../visual-basic/language-reference/modifiers/auto.md)， [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)，並[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞會停用。 語法[Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)陳述式也會修改成`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。 下列程式碼顯示的效果`-netcf`在編譯時。

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- 使用 Visual Basic 6.0 已移除從 Visual Basic 的關鍵字會產生不同的錯誤時`-netcf`用。 這會影響下列關鍵字的錯誤訊息：

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

下列程式碼編譯`Myfile.vb`使用.NET Compact Framework 中，使用 mscorlib.dll 和 Microsoft.VisualBasic.dll 的版本中找到.NET Compact Framework 的 C 磁碟機上的預設安裝目錄。 一般而言，您會使用.NET Compact Framework 的最新版本。

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
