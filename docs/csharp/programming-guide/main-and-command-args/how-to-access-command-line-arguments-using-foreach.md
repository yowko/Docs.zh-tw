---
title: "如何：使用 foreach 存取命令列引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "命令列引數 [C#]"
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)
另一個逐一查看陣列的方法，就是使用本範例中所示的 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式。  `foreach` 陳述式可以用來逐一查看陣列、.NET Framework 集合類別或實作 <xref:System.Collections.IEnumerable> 介面的任何類別或結構。  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visual-studio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## 範例  
 本範例示範如何使用 `foreach` 印出命令列引數。  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/how-to-access-command-li_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/how-to-access-command-li_2.cs)]  
  
## 請參閱  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main\(\) 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Main\(\) 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)