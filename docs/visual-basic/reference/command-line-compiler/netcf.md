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
ms.openlocfilehash: 3df7e622f97a5a1291736180e3964b1b3deaea2f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005456"
---
# <a name="-netcf"></a>-netcf

設定編譯器以 .NET Compact Framework 為目標。

## <a name="syntax"></a>語法

```console
-netcf
```

## <a name="remarks"></a>備註

@No__t-0 選項會使 Visual Basic 編譯器以 .NET Compact Framework 而不是完整 .NET Framework 為目標。 只在完整 .NET Framework 中顯示的語言功能已停用。

@No__t-0 選項是設計來搭配[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)使用。 @No__t-0 所停用的語言功能，與 `-sdkpath` 的目標檔案中不存在相同的語言功能。

> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。 載入 Visual Basic 裝置專案時，會設定 `-netcf` 選項。

@No__t-0 選項會變更下列語言功能：

- 已停用終止執行程式的[End @no__t 1keyword > 語句](../../../visual-basic/language-reference/statements/end-keyword-statement.md)關鍵字。 下列程式會編譯並執行，但不 `-netcf`，但在編譯時期會發生 `-netcf`。

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- 所有形式的晚期繫結都會停用。 遇到可識別的晚期繫結案例時，就會產生編譯時期錯誤。 下列程式會編譯並執行，但不 `-netcf`，但在編譯時期會發生 `-netcf`。

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)和[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾詞已停用。 [Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)語句的語法也會修改為 `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`。 下列程式碼顯示在編譯時 `-netcf` 的效果。

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- 使用從 Visual Basic 移除的 Visual Basic 6.0 關鍵字會在使用 `-netcf` 時產生不同的錯誤。 這會影響下列關鍵字的錯誤訊息：

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

下列程式碼會使用在 C 磁片磁碟機上 .NET Compact Framework 的預設安裝目錄中找到的 mscorlib.dll 和 default.aspx 版本，搭配 .NET Compact Framework 來編譯 `Myfile.vb`。 一般來說，您會使用最新版本的 .NET Compact Framework。

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
