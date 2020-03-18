---
title: 如何為 Visual Studio 命令列設定環境變數
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: 99e2a837877494dd4c7e0106047bce3cc39a9282
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75342357"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>如何為 Visual Studio 命令列設定環境變數

VsDevCmd.bat 檔案可設定適當的環境變數，以啟用命令列組建。

> [!NOTE]
> Visual Studio 2015 和早期版本出於相同目的使用了 VSVARS32.bat，而不是 VsDevCmd.bat。 此檔案的儲存位置為 \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools。

如果安裝最新版 Visual Studio 的電腦上也有安裝舊版 Visual Studio，請勿於相同的命令提示字元視窗中，執行不同版本的 VsDevCmd.bat 及 VSVARS32.BAT。 而是應改為在各版本本身的視窗中執行命令。

### <a name="to-run-vsdevcmdbat"></a>執行 VsDevCmd.BAT

1. 在 **"開始"** 功能表中，打開**VS 2019 的開發人員命令提示符**。  它在**Visual Studio 2019**資料夾中。

2. 更改為 [程式檔]微軟視覺化工作室\\*版本*\\*提供*[通用 7]工具或 [程式檔 （x86）\\\微軟視覺化工作室*版本*\\*提供*[公共7]工具子目錄的安裝。  （*當前版本的版本*為*2019 年*。 *供應項目*為 *Enterprise*、*Professional* 或 *Community* 中的其中一個。)

3. 鍵入 **VsDevCmd**以執行 VsDevCmd.bat。

    > [!CAUTION]
    > 在不同的電腦上，VsDevCmd.bat 檔案可能也不同。 請勿使用另一部電腦的 VsDevCmd.bat 來取代遺失或損毀的 VsDevCmd.bat 檔案。 請重新執行安裝程式以取代遺失的檔案。

### <a name="available-options-for-vsdevcmdbat"></a>適用於 VsDevCmd.BAT 的可用選項

若要查看適用於 VsDevCmd.BAT 的可用選項，請搭配 `-help` 選項執行命令：

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a>另請參閱

- [使用 csc.exe 建置命令列](./command-line-building-with-csc-exe.md)
