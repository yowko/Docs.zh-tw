---
title: "如何：在 Office 程式設計中使用具名和選擇性引數 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "具名和選擇性引數 [C#], Office 程式設計"
  - "具名引數 [C#], Office 程式設計"
  - "選擇性引數 [C#], Office 程式設計"
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 34
---
# 如何：在 Office 程式設計中使用具名和選擇性引數 (C# 程式設計手冊)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp-dev10-long-md.md)] 中引進的具名引數和選擇性引數可以加強 C\# 程式設計的方便性、彈性和可讀性。此外，這些功能還可大幅加速對 COM 介面 \(例如 Microsoft Office Automation API\) 的存取。  
  
 在下列範例中，方法 [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) 有 16 個參數，這些參數代表資料表的特性，例如欄數和列數、格式化、邊框、字型和顏色。  所有 16 個參數都是選擇性，因為大部分時間您不會想要指定每個參數的特定值。  不過，如果不使用具名和選擇性引數，則每個參數都必須提供值或預留位置值。  使用具名和選擇性引數，您只需指定專案所需的參數值。  
  
 您必須已在電腦上安裝 Microsoft Office Word，才能完成下列程序。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要建立新的主控台應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
3.  在 \[**範本類別**\] 窗格中，展開 \[**Visual C\#**\]，然後按一下 \[**Windows**\]。  
  
4.  查看 \[**範本**\] 窗格的頂端，確定 \[**.NET Framework 4**\] 顯示在 \[**目標 Framework**\] 方塊中。  
  
5.  按一下 \[**範本**\] 窗格中的 \[**主控台應用程式**\]。  
  
6.  在 \[**名稱**\] 欄位中，輸入專案的名稱。  
  
7.  按一下 \[**確定**\]。  
  
     新專案即會出現於 \[**方案總管**\] 中。  
  
### 若要加入參考  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下您的專案名稱，然後按一下 \[**加入參考**\]。  \[**加入參考**\] 對話方塊隨即出現。  
  
2.  在 \[**.NET**\] 頁面上，選取 \[**元件名稱**\] 清單中的 \[**Microsoft.Office.Interop.Word**\]。  
  
3.  按一下 \[**確定**\]。  
  
### 若要加入必要的 using 指示詞  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 \[**Program.cs**\] 檔案，再按一下 \[**檢視程式碼**\]。  
  
2.  在程式碼檔案的頂端加入下列 `using` 指示詞。  
  
     [!code-cs[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#4)]  
  
### 若要在 Word 文件中顯示文字  
  
1.  將下列方法加入至 Program.cs 的 `Program` 類別中，以便建立 Word 應用程式和 Word 文件。  [Add](http://go.microsoft.com/fwlink/?LinkId=145381) 方法有 4 個選擇性參數。  這個範例使用其預設值。  因此，呼叫陳述式中不需要引數。  
  
     [!code-cs[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#6)]  
  
2.  將下列程式碼加入至方法的結尾，定義在文件何處顯示文字，以及顯示哪些文字。  
  
     [!code-cs[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#7)]  
  
### 若要執行應用程式  
  
1.  將下列陳述式加入至 Main。  
  
     [!code-cs[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#8)]  
  
2.  按 CTRL\+F5 執行專案。  會出現一個 Word 文件，包含所指定的文字。  
  
### 若要將文字變更為表格  
  
1.  使用 `ConvertToTable` 方法，將文字框在表格中。  此方法有 16 個選擇性參數。  IntelliSense 會以括弧括住選擇性參數，如下圖所示。  
  
     ![ConvertToTable 方法的參數清單。](../../../csharp/programming-guide/classes-and-structs/media/convert-tableparameters.png "Convert\_TableParameters")  
ConvertToTable 參數  
  
     具名和選擇性引數讓您可以僅指定您要變更之參數的值。  將下列程式碼加入至 `DisplayInWord` 方法的結尾，建立簡單表格。  引數指定 `range` 中文字字串的逗號用於分隔資料表儲存格。  
  
     [!code-cs[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#9)]  
  
     在舊版 C\# 中呼叫 `ConvertToTable` 時，每個參數都需要參考引數，如以下程式碼所示。  
  
     [!code-cs[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#14)]  
  
2.  按 CTRL\+F5 執行專案。  
  
### 若要實驗其他參數  
  
1.  若要變更表格，讓它具有一欄和三列，請將 `DisplayInWord` 的最後一行改為下列陳述式，然後按 CTRL\+F5。  
  
     [!code-cs[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#10)]  
  
2.  若要指定表格的預先定義格式，請將 `DisplayInWord` 的最後一行改為下列陳述式，然後按 CTRL\+F5。  格式可以是任一 [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) 常數。  
  
     [!code-cs[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#11)]  
  
## 範例  
 下列程式碼包含完整範例。  
  
 [!code-cs[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/namedandoptionalsnippets/wordprogram.cs#12)]  
  
## 請參閱  
 [具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)