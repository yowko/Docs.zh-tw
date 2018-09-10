---
title: 如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 811ee09aec7afac70f3f2c2fe5fb002232935028
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511332"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>如何：使用 foreach 存取命令列引數 (C# 程式設計手冊)
逐一查看陣列的另一種方法是使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 陳述式，如本例所示。 `foreach` 陳述式可用來逐一查看陣列、.NET Framework 集合類別，或實作 <xref:System.Collections.IEnumerable> 介面的任何類別或結構。  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁面](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## <a name="example"></a>範例  
 本例會示範如何使用 `foreach` 印出命令列引數。  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Array>  
- <xref:System.Collections>  
- [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)  
- [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
