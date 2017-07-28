---
title: "Main() 和命令列引數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
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
ms.openlocfilehash: 1b2950f7718cda66b545935229a64850449850d0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() 和命令列引數 (C# 程式設計手冊)
`Main` 方法是 C# 主控台應用程式或 Windows 應用程式的進入點 (程式庫和服務不需要使用 `Main` 方法做為進入點)。 啟動應用程式時，`Main` 方法是第一個叫用的方法。  
  
 C# 程式中只能有一個進入點。 如果您具有多個含 `Main` 方法的類別，就必須使用 **/main** 編譯器選項來編譯您的程式，以指定要使用哪一個 `Main` 方法做為進入點。 如需詳細資訊，請參閱 [/main (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)。  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
## <a name="overview"></a>概觀  
  
-   `Main` 方法是 .exe 程式的進入點；它是程式控制開始和結束的位置。  
  
-   `Main` 會宣告於類別或結構內部。 `Main` 必須是 [static](../../../csharp/language-reference/keywords/static.md) 且不應是 [public](../../../csharp/language-reference/keywords/public.md) (在先前範例中，它會接收 [private](../../../csharp/language-reference/keywords/private.md) 的預設存取)。封入類別或結構不需要是 static。  
  
-   `Main` 可以具有 `void` 或 `int` 傳回型別。  
  
-   `Main` 方法不一定要使用包含命令列引數的 `string[]` 參數來宣告。 使用 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 來建立 Windows Forms 應用程式時，您可以手動新增參數，或使用 <xref:System.Environment> 類別來取得命令列引數。 參數會讀入來做為以零為基礎的命令列引數。 不同於 C 和 C++，程式的名稱不會被視為第一個命令列引數。  
  
## <a name="in-this-section"></a>本章節內容  
  
-   [命令列引數](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [C# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover>C# 範例應用程式](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)

