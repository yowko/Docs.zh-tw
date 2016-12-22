---
title: "逐步解說：建立和使用動態物件 (C# 和 Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "動態物件"
  - "動態物件 [C#]"
  - "動態物件 [Visual Basic]"
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 逐步解說：建立和使用動態物件 (C# 和 Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

動態物件會在執行階段 \(而非編譯階段\) 公開屬性和方法等成員。  如此一來您即可建立物件，以處理不符合靜態類型或格式的結構。  例如，您可以使用動態物件來參考 HTML 文件物件模型 \(DOM\)，而該模型可包含任意組合的有效 HTML 標記項目和屬性。  因為每一份 HTML 文件都是獨特的，所以會在執行階段決定特定 HTML 文件的成員。  有個常用於參考 HTML 項目屬性的方法，就是將屬性名稱傳遞至項目的 `GetProperty` 方法。  若要參考 HTML 項目 `<div id="Div1">` 的 `id` 屬性，請先取得 `<div>` 項目的參考，然後使用 `divElement.GetProperty("id")`。  如果您使用的是動態物件，則可以將 `id` 屬性參考為 `divElement.id`。  
  
 動態物件也提供 IronPython 和 IronRuby 等動態語言方便的存取。  您可以使用動態物件來參考在執行階段解譯的動態指令碼。  
  
 您可使用晚期繫結來參考動態物件。  在 C\# 中，您會將晚期繫結物件的類型指定為 `dynamic`。  在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，您會將晚期繫結物件的類型指定為 `Object`。  如需詳細資訊，請參閱[dynamic](../../../csharp/language-reference/keywords/dynamic.md)與[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)。  
  
 您可以使用 <xref:System.Dynamic?displayProperty=fullName> 命名空間中的類別，建立自訂動態物件。  例如，您可以在執行階段建立 <xref:System.Dynamic.ExpandoObject> 並指定該物件的成員。  您也可以建立自己的類型，該類型會繼承 <xref:System.Dynamic.DynamicObject> 類別。  您可以覆寫 <xref:System.Dynamic.DynamicObject> 類別的成員，以提供執行階段的動態功能。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立自訂物件，而該物件會以動態方式將文字檔的內容公開為物件的屬性。  
  
-   建立使用 `IronPython` 程式庫的專案。  
  
## 必要條件  
 您需要 IronPython 2.6.1 for .NET 4.0 才能完成本逐步解說。  您可以從 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) \(英文\) 下載 IronPython 2.6.1 for .NET 4.0。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## 建立自訂動態物件  
 您在這個逐步解說中建立的第一個專案會定義一個可搜尋文字檔內容的動態物件。  要搜尋的文字會依照動態屬性的名稱來指定。  例如，如果呼叫程式碼指定 `dynamicFile.Sample`，則動態類別會傳回字串泛型清單，內含檔案中所有以 "Sample" 開頭的行。  搜尋不區分大小寫。  動態類別也支援兩個選擇性引數。  第一個引數是搜尋選項列舉值，可指定動態類別應在行首、行尾或行中任意處搜尋相符項目。  第二個引數則指定動態類別應該在搜尋之前修剪每一行的前置和尾端空格。  例如，如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.Contains)`，則動態類別會在行中任意處搜尋 "Sample"。  如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.StartsWith, false)`，則動態類別會在每一行的開頭搜尋 "Sample"，但不會移除前置和尾端空格。  動態類別的預設行為是在每一行的開頭搜尋相符項目，並移除前置和尾端空格。  
  
#### 若要建立自訂動態類別  
  
1.  啟動 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。  
  
2.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
3.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 窗格中，確定已選取 \[**Windows**\]。  選取 \[**主控台應用程式**\] 中的 \[**範本**\] 窗格。  在 \[**名稱**\] 方塊中，輸入 `DynamicSample`，然後按一下 \[**確定**\]。  接著會建立新專案。  
  
4.  以滑鼠右鍵按一下 DynamicSample 專案並指向 \[**加入**\]，然後按一下 \[**類別**\]。  在 \[**名稱**\] 方塊中，輸入 `ReadOnlyFile`，然後按一下 \[**確定**\]。  會加入含有 ReadOnlyFile 類別的新檔案。  
  
5.  在 ReadOnlyFile.cs 或 ReadOnlyFile.vb 檔案的頂端，加入下列程式碼，以匯入 <xref:System.IO?displayProperty=fullName> 和 <xref:System.Dynamic?displayProperty=fullName> 命名空間。  
  
     [!code-cs[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]
     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  自訂動態物件使用列舉來決定搜尋準則。  在類別陳述式之前，加入下列列舉定義。  
  
     [!code-cs[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]
     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  更新類別陳述式以繼承 `DynamicObject` 類別，如下列程式碼範例所示。  
  
     [!code-cs[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]
     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  將下列程式碼加入至 `ReadOnlyFile` 類別，以定義檔案路徑的私用欄位以及 `ReadOnlyFile` 類別的建構函式。  
  
     [!code-cs[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. 將下列 `GetPropertyValue` 方法加入至 `ReadOnlyFile` 類別。  `GetPropertyValue` 方法會將搜尋準則當做輸入，並傳回文字檔中符合該搜尋準則的行。  `ReadOnlyFile` 類別所提供的動態方法會呼叫 `GetPropertyValue` 方法，以擷取其各自的結果。  
  
     [!code-cs[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. 在 `GetPropertyValue` 方法之後，加入下列程式碼，以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。  在要求動態類別的成員且未指定引數時，會呼叫 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。  `binder` 引數包含所參考成員的相關資訊，而 `result` 引數會參考對指定之成員傳回的結果。  如果要求的成員存在，則 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法所傳回的布林值會傳回 `true`，否則傳回 `false`。  
  
     [!code-cs[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. 在 `TryGetMember` 方法之後，加入下列程式碼，以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。  使用引數要求動態類別的成員時，會呼叫 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。  `binder` 引數包含所參考成員的相關資訊，而 `result` 引數會參考對指定之成員傳回的結果。  `args` 引數包含已傳遞給成員的引數陣列。  如果要求的成員存在，則 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法所傳回的布林值會傳回 `true`，否則傳回 `false`。  
  
     `TryInvokeMember` 方法的自訂版本預期第一個引數是您在先前步驟中定義的 `StringSearchOption` 列舉值。  `TryInvokeMember` 方法預期第二個引數是布林值。  如果其中一個引數或兩者都是有效值，則會將引數傳遞至 `GetPropertyValue` 方法，以擷取結果。  
  
     [!code-cs[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. 儲存並關閉檔案。  
  
#### 若要建立範例文字檔  
  
1.  以滑鼠右鍵按一下 DynamicSample 專案，然後指向 \[**加入**\]，再按一下 \[**新增項目**\]。  在 \[**已安裝的範本**\] 窗格中，選取 \[**一般**\]，然後選取 \[**文字檔**\] 範本。  在 \[**名稱**\] 方塊中保留 TextFile1.txt 預設名稱，然後按一下 \[**加入**\]。  新的文字檔會加入至專案中。  
  
2.  將下列文字複製到 TextFile1.txt 檔。  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  儲存並關閉檔案。  
  
#### 若要建立會使用自訂動態物件的範例應用程式  
  
1.  在 \[**方案總管**\] 中，如果使用的是 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，請按兩下 Module1.vb 檔，而如果使用的是 Visual C\#，則按兩下 Program.cs 檔。  
  
2.  將下列程式碼加入至 Main 程序，以針對 TextFile1.txt 檔建立 `ReadOnlyFile` 類別的執行個體。  此程式碼使用晚期繫結來呼叫動態成員以及擷取含有 "Customer" 字串的文字行。  
  
     [!code-cs[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  儲存檔案並且按 CTRL\+F5，以建置和執行應用程式。  
  
## 呼叫動態語言程式庫  
 在這個逐步解說中建立的下一個專案會存取一個以動態語言 IronPython 撰寫的程式庫。  您必須先安裝 IronPython 2.6.1 for .NET 4.0，才能建立這個專案。  您可以從 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) \(英文\) 下載 IronPython 2.6.1 for .NET 4.0。  
  
#### 若要建立自訂動態類別  
  
1.  在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 中的 \[**檔案**\] 功能表上，指向 \[**新增**\] 然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 窗格中，確定已選取 \[**Windows**\]。  選取 \[**主控台應用程式**\] 中的 \[**範本**\] 窗格。  在 \[**名稱**\] 方塊中輸入 `DynamicIronPythonSample`，然後按一下 \[**確定**\]。  接著會建立新專案。  
  
3.  如果您是使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，請以滑鼠右鍵按一下 DynamicIronPythonSample 專案，然後按一下 \[**屬性**\]。  按一下 \[**參考**\] 索引標籤。  按一下 \[**加入**\] 按鈕。  如果您是使用 Visual C\#，請以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**參考**\] 資料夾，然後按一下 \[**加入參考**\]。  
  
4.  在 \[**瀏覽**\] 索引標籤上，瀏覽至安裝 IronPython 程式庫的資料夾。  例如，C:\\Program Files\\IronPython 2.6 for .NET 4.0。  選取 **IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll** 和 **Microsoft.Dynamic.dll** 程式庫。  按一下 \[**確定**\]。  
  
5.  如果您是使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，請編輯 Module1.vb 檔案。  如果您是使用 Visual C\#，請編輯 Program.cs 檔案。  
  
6.  在檔案的頂端，加入下列程式碼，從 IronPython 程式庫匯入 `Microsoft.Scripting.Hosting` 和 `IronPython.Hosting` 命名空間。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  在 Main 方法中，加入下列程式碼，建立裝載 IronPython 程式庫的新 `Microsoft.Scripting.Hosting.ScriptRuntime` 物件。  `ScriptRuntime` 物件會載入 IronPython 程式庫模組 random.py。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  在載入 random.py 模組的程式碼後面，加入下列程式碼以建立整數陣列。  此陣列會傳遞至 random.py 模組的 `shuffle` 方法，這會將陣列中的值隨機排序。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. 儲存檔案並且按 CTRL\+F5，以建置和執行應用程式。  
  
## 請參閱  
 <xref:System.Dynamic?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [實作動態介面 \(外部部落格\)](http://go.microsoft.com/fwlink/?LinkId=230895)