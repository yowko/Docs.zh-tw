---
title: "命令列引數 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "命令列引數 [C#]"
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 命令列引數 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以透過下列其中一個方式定義方法，將引數傳遞給 `Main` 方法：  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  若要啟用 Windows Form 應用程式之 `Main` 方法的命令列引數，您必須手動修改 program.cs 中 `Main` 的簽章。  Windows Form 設計工具所產生的程式碼會建立一個不含輸入參數的 `Main`。  您也可以使用 <xref:System.Environment.CommandLine%2A?displayProperty=fullName> 或 <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName>，從主控台或 Windows 應用程式中的任何點來存取命令列引數。  
  
 `Main` 方法的參數是代表命令列引數的 <xref:System.String> 陣列。  通常您可以測試 `Length` 屬性來判斷引數是否存在，例如：  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 您也可以使用 <xref:System.Convert> 類別或 `Parse` 方法將字串引數轉換成數字類型。  例如，下列陳述式會使用 <xref:System.Int64.Parse%2A> 方法，將 `string` 轉換成 `long` 值：  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 也可以使用 C\# 類型的 `long`，這是 `Int64` 的別名：  
  
```  
long num = long.Parse(args[0]);  
```  
  
 您也可以使用 `Convert` 類別方法 `ToInt64` 來達成同樣的目的：  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 如需詳細資訊，請參閱 <xref:System.Int64.Parse%2A>和 <xref:System.Convert>。  
  
## 範例  
 下列範例將示範如何在主控台應用程式中使用命令列引數。  應用程式會在執行階段使用一個引數、將該引數轉換成整數，並且計算該數字的階乘。  如果沒有提供引數，應用程式會發出解釋該程式正確用法的訊息。  
  
 若要從命令提示字元編譯和執行應用程式，請執行下列步驟：  
  
1.  將下列程式碼貼上到任何文字編輯器，然後將檔案儲存為名稱為 `Factorial.cs` 的文字檔。  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  從 \[**開始**\] 畫面或 \[**開始**\] 功能表，開啟 Visual Studio 的 \[**開發人員命令提示字元**\] 視窗，然後巡覽至包含您剛建立檔案的資料夾。  
  
3.  輸入下列命令以編譯應用程式。  
  
     `csc Factorial.cs`  
  
     如果您的應用程式沒有編譯錯誤，就會建立名為 `Factorial.exe` 的可執行檔。  
  
4.  輸入以下命令計算 3 的階乘：  
  
     `Factorial 3`  
  
5.  命令產生這個輸出：`The factorial of 3 is 6.`  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visual-studio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
 如需如何使用命令列引數的其他範例，請參閱 [如何：使用命令列建立和使用組件](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 請參閱  
 <xref:System.Environment?displayProperty=fullName>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Main\(\) 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main\(\) 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [類別](../../../standard/base-types/classes.md)