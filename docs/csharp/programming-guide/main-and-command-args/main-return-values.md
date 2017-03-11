---
title: "Main() 傳回值 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Main 方法 [C#], 傳回值"
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Main() 傳回值 (C# 程式設計手冊)
`Main` 方法可以傳回 `void`：  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/main-return-values_1.cs)]  
  
 它也可以傳回 `int`：  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/main-return-values_2.cs)]  
  
 如果沒有要使用 `Main` 的傳回值，則傳回 `void` 所使用的程式碼會較為簡單。  不過，傳回整數可以讓程式將狀態資訊傳達給其他會叫用可執行檔的程式或指令碼。  下列範例顯示如何存取 `Main` 的傳回值。  
  
## 範例  
 下列範例會使用批次檔執行程式並測試 `Main` 函式的傳回值。  在 Windows 中執行程式時，任何從 `Main` 函式傳回的值都會儲存到名為 `ERRORLEVEL` 的環境變數中。  批次檔可以藉由檢查 `ERRORLEVEL` 變數判斷執行的結果。  一般來說，傳回值為零表示執行成功。  下列範例是個簡單的程式，會從 `Main` 函式傳回零。  這裡的零表示程式順利完成執行。  請將程式儲存為 MainReturnValTest.cs。  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/main-return-values_3.cs)]  
  
## 範例  
 由於這個範例使用批次檔，因此最好從命令提示字元編譯這段程式碼。  請按照 [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)中的指示啟用命令列建置，或者是從 \[**開始**\] 功能表中的 \[**Visual Studio Tools**\] 下使用 Visual Studio 命令提示字元。  從命令提示字元，巡覽至您儲存程式的資料夾。  下列命令會編譯 MainReturnValTest.cs，並產生可執行檔 MainReturnValTest.exe。  
  
 `csc MainReturnValTest.cs`  
  
 接著，建立批次檔執行 MainReturnValTest.exe 並顯示結果。  將下列程式碼貼到文字檔中，並在包含 MainReturnValTest.cs 和 MainReturnValTest.exe 的資料夾中，將其儲存為 `test.bat`。  在命令提示字元上藉由輸入 `test` 執行批次檔。  
  
 由於程式碼傳回零，因此批次檔會報告成功。  然而，如果您將 MainReturnValTest.cs 變更為傳回非零的值，然後再重新編譯程式，則後續執行批次檔時將報告失敗。  
  
```  
rem test.bat  
@echo off  
MainReturnValTest  
@if "%ERRORLEVEL%" == "0" goto good  
  
:fail  
    echo Execution Failed  
    echo return value = %ERRORLEVEL%  
    goto end  
  
:good  
    echo Execution succeeded  
    echo Return value = %ERRORLEVEL%  
    goto end  
  
:end  
```  
  
## 範例輸出  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [Main\(\) 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)