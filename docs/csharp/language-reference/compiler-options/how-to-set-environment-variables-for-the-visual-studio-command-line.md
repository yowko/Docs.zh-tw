---
title: "如何：為 Visual Studio 命令列設定環境變數"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
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
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>如何：為 Visual Studio 命令列設定環境變數

VsDevCmd.bat 檔案設定適當的環境變數來啟用命令列組建。 如需 VsDevCmd.bat 的詳細資訊，請參閱[知識庫文件 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)。  

> [!NOTE]
> VsDevCmd.bat 檔案是使用 Visual Studio 2017 傳遞新的檔案。 Visual Studio 2015 和較早版本用於相同目的 VSVARS32.bat。 此檔案儲存在 Visual Studio \Program Files\Microsoft\\*版本*\Common7\Tools 或 Program Files (x86) \Microsoft Visual Studio\\*版本*\Common7\Tools。
  
如果目前版本的 Visual Studio 也有舊版的 Visual Studio 的電腦上安裝，您不應該執行 VsDevCmd.bat 和 vsvars32 以。BAT 從相同的命令提示字元視窗中的不同版本。 相反地，您應該在它自己的視窗中執行每個版本的命令。
  
### <a name="to-run-vsdevcmdbat"></a>若要執行 VsDevCmd.BAT  
  
1.  從**啟動**功能表中，開啟**VS 2017 的開發人員命令提示字元**。  處於**Visual Studio 2017**資料夾。
  
2.  將變更為 \Program Files\Microsoft Visual Studio\\*版本*\\*供應項目*\Common7\Tools 或 \Program 檔案 (x86) \Microsoft Visual Studio\\*版本*\\*供應項目*安裝 \Common7\Tools 子目錄。  (*版本*是*2017年*目前版本。 *供應項目*是其中一個*企業*， *Professional*或*社群*。)
  
3.  輸入執行 VsDevCmd.bat **VsDevCmd**。  
  
    > [!CAUTION]
    >  VsDevCmd.bat 可以從電腦而異。 請勿使用 VsDevCmd.bat 從另一部電腦取代 VsDevCmd.bat 檔案遺失或損毀。 請重新執行安裝程式以取代遺失的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
