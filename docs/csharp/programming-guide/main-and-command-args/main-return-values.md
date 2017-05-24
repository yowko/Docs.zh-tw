---
title: "Main() 傳回值 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 846c52b7d5429a23f354dd6a732ddb62563a55bf
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="main-return-values-c-programming-guide"></a>Main() 傳回值 (C# 程式設計手冊)
`Main` 方法可以傳回 `void`：  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 它也可以傳回 `int`：  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 如果未使用來自 `Main` 的傳回值，則傳回 `void` 可允許使用比較簡單的程式碼。 不過，若是傳回一個整數，可讓程式將狀態資訊傳達給其他會叫用可執行檔的程式或指令碼。 下列範例示範如何存取來自 `Main` 的傳回值。  
  
## <a name="example"></a>範例  
 在此範例中，會使用批次檔來執行程式並測試 `Main` 函式的傳回值。 在 Windows 中執行程式時，任何從 `Main` 函式傳回的值，皆會儲存在稱為 `ERRORLEVEL` 的環境變數中。 批次檔可藉由檢查 `ERRORLEVEL` 變數，來決定執行的結果。 傳統上，傳回值為零即表示執行成功。 下列範例是一種簡單程式，其會從 `Main` 函式傳回零。 零表示已成功執行程式。 將程式儲存為 MainReturnValTest.cs。  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## <a name="example"></a>範例  
 由於此範例使用批次檔，因此最好透過命令提示字元編譯程式碼。 遵循[如何：為 Visual Studio 命令列設定環境變數](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)中的指示執行，以啟用命令列組建，或使用 Visual Studio 命令提示字元 (可從 [Visual Studio Tools]**** 下方的 [啟動]**** 功能表取得)。 從命令提示字元中，瀏覽至您之前儲存程式的資料夾。 下列命令會編譯 MainReturnValTest.cs，並產生可執行檔 MainReturnValTest.exe。  
  
 `csc MainReturnValTest.cs`  
  
 接下來，建立批次檔以執行 MainReturnValTest.exe，並顯示結果。 將下列程式碼貼入文字檔，將它儲存為 `test.bat`，並放到包含 MainReturnValTest.cs 和 MainReturnValTest.exe 的資料夾中。 在命令提示字元處鍵入 `test`，以執行批次檔。  
  
 由於程式碼會傳回零，因為批次檔會報告成功。 不過，如果您將 MainReturnValTest.cs 變更為傳回非零值，並重新編譯程式，則批次檔的後續執行階段會報告失敗。  
  
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
  
## <a name="sample-output"></a>範例輸出  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
