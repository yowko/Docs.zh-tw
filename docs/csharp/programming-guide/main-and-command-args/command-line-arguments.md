---
title: "命令列引數 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
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
ms.openlocfilehash: f0d404ae0384ec97b0eb78c6284e07cac8065548
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="command-line-arguments-c-programming-guide"></a>命令列引數 (C# 程式設計手冊)
您可以使用下列其中一種方式，透過定義方法以將引數傳送給 `Main` 方法：  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  若要在 Windows Forms 應用程式的 `Main` 方法中啟用命令列引數，您必須手動修改 program.cs 中 `Main` 的簽章。 Windows Forms 設計工具所產生的程式碼會建立沒有輸入參數的 `Main`。 您也可以使用 <xref:System.Environment.CommandLine%2A?displayProperty=fullName> 或 <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName>，以從主控台或 Windows 應用程式的任何點存取命令列引數。  
  
 `Main` 方法的參數是代表命令列引數的 <xref:System.String> 陣列。 您通常會透過測試 `Length` 屬性來決定引數是否存在，例如：  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 您也可以使用 <xref:System.Convert> 類別或 `Parse` 方法，將字串引數轉換為數字類型。 例如，下列陳述式將使用 <xref:System.Int64.Parse%2A> 方法，以將 `string` 轉換為 `long` 數字：  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 也可能使用別名為 `Int64` 的 C# 類型 `long`：  
  
```  
long num = long.Parse(args[0]);  
```  
  
 您還可以使用 `Convert` 類別方法 `ToInt64` 執行相同作業：  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 如需詳細資訊，請參閱 <xref:System.Int64.Parse%2A> 與 <xref:System.Convert>。  
  
## <a name="example"></a>範例  
 下列範例示範如何在主控台應用程式中使用命令列引數。 應用程式會在執行階段接受一個引數，並將引數轉換為整數，以及計算數字的階乘。 如果未提供任何引數，則應用程式會發出說明程式正確用法的訊息。  
  
 若要從命令提示字元編譯和執行應用程式，請遵循下列步驟︰  
  
1.  將下列程式碼貼入任何文字編輯器，然後將檔案儲存為名稱為 `Factorial.cs` 的文字檔案。  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  從 [開始] 畫面或 [開始] 功能表中，開啟 Visual Studio [開發人員命令提示字元] 視窗，然後巡覽至包含剛剛建立之檔案的資料夾。  
  
3.  輸入下列命令以編譯應用程式。  
  
     `csc Factorial.cs`  
  
     如果您的應用程式沒有任何編譯錯誤，則會建立名為 `Factorial.exe` 的可執行檔。  
  
4.  輸入下列命令以計算 3 的階乘：  
  
     `Factorial 3`  
  
5.  命令會產生以下輸出：`The factorial of 3 is 6.`  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁面](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
 如需如何使用命令列引數的其他範例，請參閱[如何：使用命令列建立和使用組件](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Environment?displayProperty=fullName>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [如何：顯示命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)

