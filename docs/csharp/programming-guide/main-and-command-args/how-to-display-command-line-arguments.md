---
title: "如何：顯示命令列引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e46860ecc2f5062abb440a764443ecee19c5153d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>如何：顯示命令列引數 (C# 程式設計手冊)
提供給命令列上可執行檔的引數，可以透過 `Main` 的選擇性參數來存取。 引數是以字串陣列的形式提供。 陣列的每個項目都包含一個引數。 引數之間的空白字元會被移除。 例如，請考慮這些虛擬可執行檔的命令列引動過程：  
  
|命令列上的輸入|傳遞至 Main 的字串陣列|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## <a name="example"></a>範例  
 此範例顯示傳遞至命令列應用程式的命令列引數。 所顯示的輸出是上表中的第一個項目。  
  
 [!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
