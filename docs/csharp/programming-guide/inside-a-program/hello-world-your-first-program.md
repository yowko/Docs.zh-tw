---
title: "Hello World -- 您的第一個程式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "get-started-article"
f1_keywords: 
  - "cs.program"
  - "vs.csharp.startpage.firstapplication"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "範例 [C#], Hello World"
  - "Hello World 範例 [C#]"
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 39
---
# Hello World -- 您的第一個程式 (C# 程式設計手冊)
下列程序會建立 C\# 版本的傳統 "Hello World\!" 程式。  程式會顯示 `Hello World!` 字串  
  
 如需介紹性概念的其他範例，請參閱[Visual C\# 和 Visual Basic 使用者入門](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要建立和執行主控台應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在功能表列上，選擇 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即開啟。  
  
3.  展開 \[**安裝**\]，展開 \[**範本**\]，展開 \[**Visual C\#**\]，然後選取 \[**主控台應用程式**\]。  
  
4.  在 \[**名稱**\] 方塊中指定專案的名稱，然後選擇 \[**確定**\] 按鈕。  
  
     新專案即會出現於 \[**方案總管**\] 中。  
  
5.  如果 Program.cs 沒有在 \[**程式碼編輯器**\] 中開啟，請在 \[**方案總管**\] 中開啟 **Program.cs** 的捷徑功能表，然後選擇 \[**檢視程式碼**\]。  
  
6.  以下列程式碼取代 Program.cs 的內容。  
  
     [!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#21)]  
  
7.  選擇 F5 鍵以執行專案。  命令提示字元視窗會出現，其中包含 `Hello World!` 一列。  
  
 接下來，則會檢查此程式的重要部分。  
  
## 註解  
 第一行包含註解。  字元 `//` 可以將這行的後面部分轉換成註解。  
  
 [!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#32)]  
  
 您也可以藉由將文字區塊封入 `/*` 和 `*/` 字元，將該文字區塊標記為註解。  這在下列範例中顯示。  
  
 [!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#33)]  
  
## Main 方法  
 C\# 主控台應用程式必須包含 `Main` 方法，以便控制項在其中開始和結束。  您可以在 `Main` 方法中建立物件和執行其他方法。  
  
 `Main` 方法是位於類別或結構內的[static](../../../csharp/language-reference/keywords/static.md) 方法。  在上一個 "Hello World\!" 範例中，它常駐在名為 `Hello` 的類別中。  您可以以下列其中一種方式宣告 `Main` 方法：  
  
-   它可以傳回 `void`。  
  
     [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/hello-world-your-first-p_4.cs)]  
  
-   它也可以傳回整數。  
  
     [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/hello-world-your-first-p_5.cs)]  
  
-   對於任一種傳回類型，都可使用引數。  
  
     [!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/hello-world-your-first-p_6.cs)]  
  
     \-或\-  
  
     [!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/hello-world-your-first-p_7.cs)]  
  
 `Main` 方法的參數 `args` 是 `string` 陣列，其中包含用來叫用程式的命令列引數。  不像在 C \+ \+，陣列並不包含可執行檔 \(exe\) 的名稱。  
  
 如需如何使用命令列引數的詳細資訊，請參閱 [Main\(\) 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 和 [如何：使用命令列建立和使用組件](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md) 中的範例。  
  
 在 `Main` 方法的結尾呼叫 <xref:System.Console.ReadKey%2A>，可避免主控台視窗在您按 F5 以偵錯模式執行，進而有機會讀取輸出之前關閉。  
  
## 輸入和輸出  
 C\# 程式通常使用由 .NET Framework 的執行階段程式庫所提供的輸入\/輸出服務。  `System.Console.WriteLine("Hello World!");` 陳述式使用 <xref:System.Console.WriteLine%2A> 方法。  這是執行階段程式庫中 <xref:System.Console> 類別的輸出方法之一。  它會在其後緊接新的一行之標準輸出資料流中，顯示它的字串參數。  其他 <xref:System.Console> 方法則可在不同的輸入和輸出作業使用。  如果您在程式的開頭加入 `using System;` 指示詞，就可以直接使用 <xref:System> 類別和方法，而無須指定完整的名稱。  例如，您可以呼叫 `Console.WriteLine` 而非 `System.Console.WriteLine`：  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/using.cs#1)]  
  
 [!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/csProgGuide/progGuide.cs#23)]  
  
 如需輸入\/輸出方法的詳細資訊，請參閱 <xref:System.IO>。  
  
## 命令列編譯及執行  
 您可以使用命令列編譯 "Hello, World\!" 程式，而不使用 Visual Studio 整合式開發環境 \(IDE\)。  
  
#### 若要編譯並從命令提示字元執行  
  
1.  從之前程序中所示的程式碼貼上到任何文字編輯器，然後將檔案儲存為文字檔。  將檔案命名為 `Hello.cs`。  C\# 原始程式碼檔案使用附加檔名 `.cs`。  
  
2.  執行下列其中一個步驟，開啟命令提示字元視窗：  
  
    -   在 Windows 8 中，於 \[**開始**\] 畫面搜尋`開發人員命令提示字元`，然後點選或選擇 \[**適用於 VS2012 的開發人員命令提示字元**\]。  
  
         \[開發人員命令提示字元\] 視窗隨即出現。  
  
    -   在 Windows 7 中，開啟 \[**開始**\] 功能表，展開 Visual Studio 最新版本的資料夾，開啟 \[**Visual Studio Tools**\] 的捷徑功能表，然後選擇 \[**適用於 VS2012 的開發人員命令提示字元**\]。  
  
         \[開發人員命令提示字元\] 視窗隨即出現。  
  
    -   從標準命令提示字元視窗中啟用命令列建置。  
  
         請參閱 [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)。  
  
3.  在命令提示字元視窗中，巡覽至包含 `Hello.cs` 檔案的資料夾。  
  
4.  輸入下列命令以編譯 `Hello.cs`。  
  
     `csc Hello.cs`  
  
     如果您的程式沒有編譯錯誤，就會建立名為 `Hello.exe` 的可執行檔。  
  
5.  在命令提示字元視窗中，輸入下列命令以執行程式：  
  
     `Hello`  
  
 如需 C\# 編譯器及其選項的詳細資訊，請參閱 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)。  
  
## 精選書籍章節  
 [初探 Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214) 中的[撰寫 C\# 程式](http://go.microsoft.com/fwlink/?LinkId=221227) \(英文\)  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 程式內部](../../../csharp/programming-guide/inside-a-program/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)   
 [\<paveover\>C\# Sample Applications](http://msdn.microsoft.com/zh-tw/9a9d7aaa-51d3-4224-b564-95409b0f3e15)   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [Main\(\) 和命令列引數](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Visual C\# 和 Visual Basic 使用者入門](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)