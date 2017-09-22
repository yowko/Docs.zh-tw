---
title: "逐步解說：建立和使用動態物件 (C# 和 Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
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
ms.sourcegitcommit: d74c1d0760d4e776c2cf4c7dea1dac060c85a83c
ms.openlocfilehash: 19701ede37845249cf4d50a34eb4ab487cdeb76b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a>逐步解說：建立和使用動態物件 (C# 和 Visual Basic)
動態物件會在執行階段公開成員 (例如屬性和方法)，而不是在編譯時期。 這可讓您建立物件，以使用與靜態類型或格式不相符的結構。 例如，您可以使用動態物件來參考 HTML 文件物件模型 (DOM)，其可包含任何有效的 HTML 標記項目和屬性組合。 由於每個 HTML 文件都是唯一的，因此系統會在執行階段決定特定的 HTML 文件成員。 參考 HTML 項目屬性的常用方法，是將屬性名稱傳遞給項目的 `GetProperty` 方法。 若要參考 HTML 項目 `<div id="Div1">` 的 `id` 屬性，您必須先取得 `<div>` 項目的參考，然後再使用 `divElement.GetProperty("id")`。 如果您使用動態物件，則能以 `divElement.id` 的形式來參考 `id` 屬性。  
  
 動態物件也可讓您方便存取動態語言 (例如 IronPython 和 IronRuby)。 您可以使用動態物件，參考在執行階段受到解譯的動態指令碼。  
  
 您可以使用晚期繫結來參考動態物件。 在 C# 中，您可以將晚期繫結物件的類型指定為 `dynamic`。 在 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 中，您可以將晚期繫結物件的類型指定為 `Object`。 如需詳細資訊，請參閱 [dynamic](../../../csharp/language-reference/keywords/dynamic.md) 與[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。  
  
 您可以在 <xref:System.Dynamic?displayProperty=fullName> 命名空間中使用類別，以建立自訂動態物件。 例如，您可以建立 <xref:System.Dynamic.ExpandoObject>，並在執行階段中指定該物件的成員。 您也可以建立繼承 <xref:System.Dynamic.DynamicObject> 類別的專屬類型。 接著，您即可覆寫 <xref:System.Dynamic.DynamicObject> 類別的成員，以提供執行階段動態功能。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立自訂物件，以將文字檔內容動態公開為物件的屬性。  
  
-   建立專案，以使用 `IronPython` 程式庫。  
  
## <a name="prerequisites"></a>必要條件  
 您需具備 IronPython 2.6.1 for .NET 4.0，才能完成此逐步解說。 您可以從 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) 下載 IronPython 2.6.1 for .NET 4.0。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a>建立自訂的動態物件  
 您在本逐步解說中建立的第一個專案，會定義自訂的動態物件，以搜尋文字檔的內容。 動態屬性的名稱可指定要搜尋的文字。 例如，如果呼叫程式碼指定 `dynamicFile.Sample`，動態類別會傳回字串的泛型清單，其中包含檔案中開頭為 "Sample" 的所有行。 搜尋不區分大小寫。 動態類別也支援兩個選擇性引數。 第一個引數是搜尋選項列舉值，它指定動態類別應該在行開頭、行結尾或行的任何位置搜尋相符項目。 第二個引數指定動態類別應該先修剪文字的前置和後端空格，再進行搜尋。 例如，如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.Contains)`，動態類別即會在行的任何位置搜尋 "Sample"。 如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.StartsWith, false)`，則動態類別會在每一行開頭搜尋 "Sample"，且不會移除前置和後端空格。 動態類別的預設行為是在每一行開頭搜尋相符項目，並移除前置和後端空格。  
  
#### <a name="to-create-a-custom-dynamic-class"></a>建立自訂動態類別  
  
1.  啟動 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]。  
  
2.  在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。  
  
3.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 選取 [範本] 窗格中的 [主控台應用程式]。 在 [名稱] 方塊中，輸入 `DynamicSample` 並按一下 [確定]。 隨即會建立新專案。  
  
4.  以滑鼠右鍵按一下 DynamicSample 專案，再指向 [新增]，然後按一下 [類別]。 在 [名稱] 方塊中，輸入 `ReadOnlyFile` 並按一下 [確定]。 隨即新增檔案，其中包含 ReadOnlyFile 類別。  
  
5.  在 ReadOnlyFile.cs 或 ReadOnlyFile.vb 檔案頂端，新增下列程式碼以匯入 <xref:System.IO?displayProperty=fullName> 和 <xref:System.Dynamic?displayProperty=fullName> 命名空間。  
  
     [!code-cs[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_1.cs)]

     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_1.vb)]  
  
6.  自訂動態物件會使用列舉來判斷搜尋準則。 在 class 陳述式之前，加入下列列舉定義。  
  
     [!code-cs[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_2.cs)]

     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_2.vb)]  
  
7.  如下列程式碼範例所示，更新繼承 `DynamicObject` 類別的 class 陳述式。  
  
     [!code-cs[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_3.cs)]

     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_3.vb)]  
  
8.  將下列程式碼新增至 `ReadOnlyFile` 類別，以定義檔案路徑的私用欄位和 `ReadOnlyFile` 類別的建構函式。  
  
     [!code-cs[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_4.cs)]
     
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_4.vb)]  
  
9. 將下列 `GetPropertyValue` 方法加入至 `ReadOnlyFile` 類別。 `GetPropertyValue` 方法會以輸入形式採用搜尋準則，並傳回文字檔中符合搜尋條件的幾行內容。 `ReadOnlyFile` 類別所提供的動態方法會呼叫 `GetPropertyValue` 方法，以擷取其各自的結果。  
  
     [!code-cs[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_5.cs)]
     
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_5.vb)]  
  
10. 在 `GetPropertyValue` 方法後面，新增下面程式碼以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。 如果系統要求動態類別的成員，但未指定任何參數，則會呼叫 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。 `binder` 引數包含參考成員的相關資訊，而 `result` 引數會參考指定成員傳回的結果。 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法會傳回布林值：如果要求的成員存在，該值會傳回 `true`；否則會傳回 `false`。  
  
     [!code-cs[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_6.cs)]
     
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_6.vb)]  
  
11. 在 `TryGetMember` 方法後面，新增下面程式碼以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。 如果系統要求具有引數的動態類別成員，則會呼叫 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。 `binder` 引數包含參考成員的相關資訊，而 `result` 引數會參考指定成員傳回的結果。 `args` 引數包含傳遞給該成員的引數陣列。 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法會傳回布林值：如果要求的成員存在，該值會傳回 `true`；否則會傳回 `false`。  
  
     自訂版 `TryInvokeMember` 方法需要的第一個引數，是來自上一個步驟所定義的 `StringSearchOption` 列舉。 `TryInvokeMember` 方法需要的第二個引數是布林值。 如果這兩個引數有一個或兩個是有效的值，即會將它們傳遞給 `GetPropertyValue` 方法以擷取結果。  
  
     [!code-cs[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_7.cs)]
     
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_7.vb)]  
  
12. 儲存並關閉檔案。  
  
#### <a name="to-create-a-sample-text-file"></a>建立範例文字檔  
  
1.  以滑鼠右鍵按一下 DynamicSample 專案，再指向 [新增]，然後按一下 [新增項目]。 在 [已安裝的範本] 窗格中，選取 [一般]，然後選取 [文字檔] 範本。 保留 [名稱] 方塊中的 TextFile1.txt 預設名稱，然後按一下 [新增]。 新的文字檔隨即加入專案中。  
  
2.  將下列文字複製到 TextFile1.txt 檔案。  
  
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
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a>建立使用自訂動態物件的範例應用程式  
  
1.  在 [方案總管] 中，如果您是使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，請按兩下 Module1.vb 檔案，或者，如果您是使用 Visual C#，請按兩下 Program.cs 檔案。  
  
2.  將下列程式碼加入 Main 程序，以為 TextFile1.txt 檔案建立 `ReadOnlyFile` 類別的執行個體。 程式碼會使用晚期繫結呼叫動態成員，並擷取包含字串 "Customer" 的文字行。  
  
     [!code-cs[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_8.cs)]
     
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_8.vb)]  
  
3.  儲存檔案，並按 CTRL+F5 建置及執行應用程式。  
  
## <a name="calling-a-dynamic-language-library"></a>呼叫動態語言程式庫  
 您在本逐步解說中建立的下一個專案，會存取以動態語言 IronPython 撰寫的程式庫。 建立此專案之前，您必須先安裝 IronPython 2.6.1 for .NET 4.0 。 您可以從 [CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) 下載 IronPython 2.6.1 for .NET 4.0。  
  
#### <a name="to-create-a-custom-dynamic-class"></a>建立自訂動態類別  
  
1.  在 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 的 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 選取 [範本] 窗格中的 [主控台應用程式]。 在 [名稱] 方塊中，輸入 `DynamicIronPythonSample` 並按一下 [確定]。 隨即會建立新專案。  
  
3.  如果您是使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，請以滑鼠右鍵按一下 DynamicIronPythonSample 專案，然後按一下 [屬性]。 按一下 [參考] 節點。按一下 [新增] 按鈕。 如果您是使用 Visual C#，請在 [方案總管] 中，以滑鼠右鍵按一下 [參考] 資料夾，然後按一下 [加入參考]。  
  
4.  在 [瀏覽] 索引標籤上，瀏覽至安裝 IronPython 程式庫的資料夾。 例如 C:\Program Files\IronPython 2.6 for .NET 4.0。 選取 **IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll** 和 **Microsoft.Dynamic.dll** 程式庫。 按一下 [確定]。  
  
5.  如果您是使用 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]，請編輯 Module1.vb 檔案。 如果您是使用 Visual C#，請編輯 Program.cs 檔案。  
  
6.  在檔案頂端，加入下列程式碼以匯入來自 IronPython 程式庫的 `Microsoft.Scripting.Hosting` 和 `IronPython.Hosting` 命名空間。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_9.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_9.vb)]  
  
7.  在 Main 方法中加入下列程式碼，以建立裝載 IronPython 程式庫的新 `Microsoft.Scripting.Hosting.ScriptRuntime` 物件。 `ScriptRuntime` 物件會載入 IronPython 程式庫模組 random.py。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_10.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_10.vb)]  
  
8.  在程式碼載入 random.py 模組之後，請加入下列程式碼以建立整數陣列。 系統會將陣列傳遞給 random.py 模組的 `shuffle` 方法，其會隨機排序陣列中的值。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/CSharp/walkthrough-creating-and-using-dynamic-objects_11.cs)]
     
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/VisualBasic/walkthrough-creating-and-using-dynamic-objects_11.vb)]  
  
9. 儲存檔案，並按 CTRL+F5 建置及執行應用程式。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Dynamic?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [實作動態介面 (外部部落格)](http://go.microsoft.com/fwlink/?LinkId=230895)

