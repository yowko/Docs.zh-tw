---
title: "如何：為 Visual Studio 命令列設定環境變數"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
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
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 569683169c6d7ae50c33ed06d3b365a663f16715
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>如何：為 Visual Studio 命令列設定環境變數
vsvars32.bat 檔可設定適當的環境變數，以啟用命令列組建。 如需 vsvars32.bat 的詳細資訊，請參閱[知識庫文章 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)。  
  
 如果安裝最新版 Visual Studio 的電腦上也有安裝舊版 Visual Studio，請不要在同一個 [命令提示字元] 視窗中，執行不同版本的 vsvars32.bat 或 vcvars32.bat。  
  
### <a name="to-run-vsvars32bat"></a>執行 VSVARS32.BAT  
  
1.  從 [開始] 功能表中，開啟 [適用於 VS2012 的開發人員命令提示字元]。  
  
2.  根據您的安裝變更到 Program Files\Microsoft Visual Studio *Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio *Version*\Common7\Tools 子目錄。  
  
3.  輸入 **VSVARS32** 以執行 VSVARS32.bat。  
  
    > [!CAUTION]
    >  在不同的電腦上，VSVARS32.bat 檔案可能也不同。 請不用使用其他電腦上的 VSVARS32.bat，來取代遺失或損毀的 VSVARS32.bat 檔案。 請重新執行安裝程式以取代遺失的檔案。  
  
## <a name="see-also"></a>另請參閱  
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)

