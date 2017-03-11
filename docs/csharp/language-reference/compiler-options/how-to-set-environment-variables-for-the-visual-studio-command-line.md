---
title: "How to: Set Environment Variables for the Visual Studio Command Line | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cs.build.commandline"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "csc.exe, command-line builds"
  - "Visual C#, command-line builds"
  - "command-line compilers, Visual C#"
  - "Vsvars32.bat"
  - "builds [C#], command-line"
  - "compilers, invoking from command line"
  - "Vcvars32.bat file"
  - "command line [C#], building from"
  - "Visual C# compiler, enabling"
  - "compiling source code, from command line"
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# How to: Set Environment Variables for the Visual Studio Command Line
vsvars32.bat 檔可設定適當的環境變數，以啟用命令列組建。  如需 vsvars32.bat 的詳細資訊，請參閱[知識庫文件 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)。  
  
 如果安裝最新版 Visual Studio 的電腦上也有安裝舊版 Visual Studio，請不要在同一個 \[命令提示字元\] 視窗中，執行不同版本的 vsvars32.bat 或 vcvars32.bat。  
  
### 執行 VSVARS32.BAT  
  
1.  從 \[**啟動**\] 功能表中，開啟 \[**VS2012 開發人員命令提示字元**\]。  
  
2.  根據您的安裝變更到 Program Files\\Microsoft Visual Studio *Version*\\Common7\\Tools 或 Program Files \(x86\)\\Microsoft Visual Studio *Version*\\Common7\\Tools 子目錄。  
  
3.  輸入 VSVARS32 以執行 VSVARS32.bat。  
  
    > [!CAUTION]
    >  在不同的電腦上，VSVARS32.bat 檔案可能也不同。  請不用使用其他電腦上的 VSVARS32.bat，來取代遺失或損毀的 VSVARS32.bat 檔案。  請重新執行安裝程式以取代遺失的檔案。  
  
## 請參閱  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)