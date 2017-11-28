---
title: "如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)
逐一查看陣列的另一種方法是使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，如本例所示。 `foreach` 陳述式可用來逐一查看陣列、.NET Framework 集合類別，或實作 <xref:System.Collections.IEnumerable> 介面的任何類別或結構。  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁面](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## <a name="example"></a>範例  
 本例會示範如何使用 `foreach` 印出命令列引數。  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Array>  
 <xref:System.Collections>  
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
