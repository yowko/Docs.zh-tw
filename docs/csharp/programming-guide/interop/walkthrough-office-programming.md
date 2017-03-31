---
title: "逐步解說：Office 程式設計 (C# 和 Visual Basic) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
caps.latest.revision: 46
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
ms.openlocfilehash: f93a5403660ca850d6650a1a6406395dfa2cc2e5
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a>逐步解說：Office 程式設計 (C# 和 Visual Basic)
Visual Studio 在 C# 和 Visual Basic 中開始採用改善 Microsoft Office 程式設計的新功能。 每一種語言都已經加入其他語言的現有功能。  
  
 C# 中的新功能包含具名及選擇性引數、類型為 `dynamic` 的傳回值，以及 COM 程式設計中省略 `ref` 關鍵字以及存取已編製索引之屬性的能力。 Visual Basic 中的新功能包含自動實作的屬性、Lambda 運算式中的陳述式，以及集合初始設定式。  
  
 這兩種語言都會啟用類型資訊的內嵌，以允許部署與 COM 元件互動的組件，而不需要將主要 Interop 組件 (PIA) 部署至使用者電腦。 如需詳細資訊，請參閱[逐步解說：從 Managed 組件內嵌類型 (C# 和 Visual Basic)](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)。  
  
 這個逐步解說將會示範 Office 程式設計內容中的新功能，但其中大部分也適用於一般的程式設計。 在這個逐步解說中，您會先使用 Excel 增益集應用程式來建立 Excel 活頁簿。 接著，您會建立含有活頁簿連結的 Word 文件。 最後，您會看到如何開啟和關閉 PIA 相依性。  
  
## <a name="prerequisites"></a>必要條件  
 您必須已在電腦上安裝 Microsoft Office Excel 2013 (或 2007 版或更新版本) 以及 Microsoft Office Word 2013 (或 2007 版或更新版本)，才能完成這個逐步解說。  
  
 如果您使用 [!INCLUDE[windowsver](../../../csharp/programming-guide/interop/includes/windowsver_md.md)] 以前的作業系統，請確定已安裝 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)]。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-set-up-an-excel-add-in-application"></a>設定 Excel 增益集應用程式  
  
1.  啟動 Visual Studio。  
  
2.  在 [檔案] **** 功能表中，指向 [新增] ****，然後按一下 [專案] ****。  
  
3.  在 [已安裝的範本]**** 窗格中，展開 [Visual Basic]**** 或 [Visual C#]****，並展開 [Office]****，然後按一下 [2013]**** (或 [2010]**** 或 [2007]****)。  
  
4.  在 [範本]**** 窗格中，按一下 [Excel 2013 增益集]**** (或 [Excel 2010 增益集]**** 或 [Excel 2007 增益集]****)。  
  
5.  查看 [範本]**** 窗格頂端，確定 **.NET Framework 4** 或更新版本出現在 [目標 Framework]**** 方塊中。  
  
6.  視需要在 [名稱]**** 方塊中，輸入您專案的名稱。  
  
7.  按一下 [確定]****。  
  
8.  新的專案隨即會出現在方案總管****中。  
  
### <a name="to-add-references"></a>加入參考  
  
1.  在方案總管****中，於專案名稱上按一下滑鼠右鍵，然後按一下 [新增參考]****。 [新增參考]**** 對話方塊隨即出現。  
  
2.  在 [組件]**** 索引標籤上，選取 **Microsoft.Office.Interop.Excel** 15.0.0.0 版 (或 Excel 2010 14.0.0.0 版或 Excel 2007 12.0.0.0 版)，並在 [元件名稱]**** 清單中，按住 CTRL 鍵，然後選取 **Microsoft.Office.Interop.Word** 15.0.0.0 版 (或 Word 2010 14.0.0.0 版或 Word 2007 12.0.0.0 版)。  如果看不到組件，您可能需要確定它們已安裝並已顯示 (請參閱[如何：安裝 Office 主要 Interop 組件](http://msdn.microsoft.com/library/92948fcc-76c6-4b08-ba63-cab59dd60eb1))。  
  
3.  按一下 [確定]****。  
  
### <a name="to-add-necessary-imports-statements-or-using-directives"></a>加入必要的 Imports 陳述式或 using 指示詞  
  
1.  在方案總管****中，以滑鼠右鍵按一下 **ThisAddIn.vb** 或 **ThisAddIn.cs** 檔案，然後按一下 [檢視程式碼]****。  
  
2.  將下列 `Imports` 陳述式 (Visual Basic) 或 `using` 指示詞 (C#) 加入還沒有這兩者的程式碼檔案頂端。  
  
     [!code-cs[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_1.cs)]
     [!code-vb[csOfficeWalkthrough#1](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_1.vb)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a>建立銀行帳戶清單  
  
1.  在方案總管****中，以滑鼠右鍵按一下您的專案名稱，再按一下 [新增]****，然後按一下 [類別]****。 如果您使用 Visual Basic，請將類別命名為 Account.vb；如果您使用 C#，則請將類別命名為 Account.cs。 按一下 [加入] ****。  
  
2.  將 `Account` 類別的定義取代為下列程式碼。 類別定義會使用 Visual Studio 2010 中 Visual Basic 的「自動實作屬性」**新功能。 如需詳細資訊，請參閱[自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。  
  
     [!code-cs[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_2.cs)]
     [!code-vb[csOfficeWalkthrough#2](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_2.vb)]  
  
3.  若要建立含有兩個帳戶的 `bankAccounts` 清單，請將下列程式碼加入 ThisAddIn.vb 或 ThisAddIn.cs 中的 `ThisAddIn_Startup` 方法。 清單宣告會使用 Visual Studio 2010 中 Visual Basic 的「集合初始設定式」**新功能。 如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。  
  
     [!code-cs[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_3.cs)]
     [!code-vb[csOfficeWalkthrough#3](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_3.vb)]  
  
### <a name="to-export-data-to-excel"></a>將資料匯出至 Excel  
  
1.  在相同的檔案中，將下列方法加入 `ThisAddIn` 類別。 這個方法會設定 Excel 活頁簿，並將資料匯出到 Excel 活頁簿。  
  
     [!code-cs[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_4.cs)]
     [!code-vb[csOfficeWalkthrough#4](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_4.vb)]  
  
     在這個方法中，使用了兩個新的 C# 功能。 這兩個功能已存在於 Visual Basic 中。  
  
    -   [Add](http://go.microsoft.com/fwlink/?LinkId=210910) 方法提供用來指定特定範本的選擇性參數**。 如果您想要使用參數的預設值，則可利用選擇性參數 ([!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 中的新功能) 省略該參數的引數。 因為上一個範例中未傳送引數，所以 `Add` 會使用預設範本並建立新的活頁簿。 舊版 C# 中對等的陳述式需要有預留位置引數：`excelApp.Workbooks.Add(Type.Missing)`。  
  
         如需詳細資訊，請參閱[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)。  
  
    -   [Range](http://go.microsoft.com/fwlink/?LinkId=210911) 物件的 `Range` 和 `Offset` 屬性會使用「編製過索引的屬性」**功能。 您可利用這項功能使用下列一般 C# 語法，來使用 COM 類型的這些屬性。 您可利用編製過索引的屬性，使用 `Value` 物件的 `Range` 屬性，而不需要使用 `Value2` 屬性。 `Value` 屬性編製過索引，但您可選擇是否要編製索引。 在下列範例中，同時使用了選擇性引數與編製過索引的屬性。  
  
         [!code-cs[csOfficeWalkthrough#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_5.cs)]  
  
         在舊版語言中，需要下列特殊語法。  
  
         [!code-cs[csOfficeWalkthrough#6](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_6.cs)]  
  
         您無法建立自己本身的編製過索引的屬性。 這個功能僅支援使用現有已編製過索引的屬性。  
  
         如需詳細資訊，請參閱[如何：在 COM Interop 程式設計中使用已編製索引的屬性](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)。  
  
2.  在 `DisplayInExcel` 結尾加入下列程式碼，以調整資料行寬度以容納內容。  
  
     [!code-cs[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_7.cs)]
     [!code-vb[csOfficeWalkthrough#7](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_7.vb)]  
  
     這些新增內容可示範 C# 2010 中的另一項新功能：將 COM 主機 (例如 Office) 傳回的 `Object` 值，視為具有 [dynamic](../../../csharp/language-reference/keywords/dynamic.md) 類型。 如果已將 [內嵌 Interop 類型]**** 設定為其預設值 `True`，則會自動發生這種情況；同樣地，當 [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 編譯器選項參考了組件時也會如此。 `dynamic` 類型可以進行晚期繫結 (Visual Basic 中已有這個功能)，並避免在 Visual C# 2008 和語言舊版本中需要明確轉型。  
  
     例如，`excelApp.Columns[1]` 會傳回 `Object`；而 `AutoFit` 則為 Excel [Range](http://go.microsoft.com/fwlink/?LinkId=210911) 方法。 如果沒有 `dynamic`，則在呼叫 `excelApp.Columns[1]` 方法之前，必須將 `Range` 所傳回的物件，轉型為 `AutoFit` 執行個體。  
  
     [!code-cs[csOfficeWalkthrough#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_8.cs)]  
  
     如需內嵌 Interop 類型的詳細資訊，請參閱本主題稍後的＜尋找 PIA 參考＞和＜還原 PIA 相依性＞程序。 如需 `dynamic` 的詳細資訊，請參閱 [dynamic](../../../csharp/language-reference/keywords/dynamic.md) 或[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。  
  
### <a name="to-invoke-displayinexcel"></a>叫用 DisplayInExcel  
  
1.  在 `ThisAddIn_StartUp` 方法的結尾，加入下列程式碼。 `DisplayInExcel` 呼叫包含兩個引數。 第一個引數是要處理的帳戶清單名稱。 第二個引數則是多行的 Lambda 運算式，定義如何處理資料。 每個帳戶的 `ID` 和 `balance` 值都會顯示在相鄰的儲存格中，而且如果餘額小於零，則會以紅色顯示資料列。 多行 Lambda 運算式是 Visual Basic 2010 中的新功能。 如需詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。  
  
     [!code-cs[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_9.cs)]
     [!code-vb[csOfficeWalkthrough#9](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_9.vb)]  
  
2.  若要執行程式，請按 F5 鍵。 隨即會出現內含帳戶資料的 Excel 工作表。  
  
### <a name="to-add-a-word-document"></a>加入 Word 文件  
  
1.  在 `ThisAddIn_StartUp` 方法的結尾加入下列程式碼，可以建立內含 Excel 活頁簿連結的 Word 文件。  
  
     [!code-cs[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_10.cs)]
     [!code-vb[csOfficeWalkthrough#10](../../../csharp/programming-guide/interop/codesnippet/VisualBasic/walkthrough-office-programming_10.vb)]  
  
     這個程式碼將會示範 C# 中的數個新功能：省略 COM 程式設計中 `ref` 關鍵字、具名引數和選擇性引數的能力。 Visual Basic 中已有這些功能。 [PasteSpecial](http://go.microsoft.com/fwlink/?LinkId=147099) 方法有七個參數，全部都定義為選擇性參考參數。 在 Visual C# 2010 之前，您必須定義物件變數以用做為七個參數的引數，即使您沒有要傳入任何有意義的值也是一樣。 您可利用具名引數和選擇性引數，指定想要依名稱存取的參數，以及將引數只傳送給那些參數。 在這個範例中會傳送引數，表示應建立剪貼簿上的活頁簿連結 (參數 `Link`)，且連結會以圖示形式顯示在 Word 文件中 (參數 `DisplayAsIcon`)。 在 Visual C# 2010 中也可省略這些引數的 `ref` 關鍵字。 請比對 Visual C# 2008 中的下列程式碼片段與 Visual C# 2010 中所需的單一行：  
  
     [!code-cs[csOfficeWalkthrough#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/walkthrough-office-programming_11.cs)]  
  
### <a name="to-run-the-application"></a>若要執行應用程式  
  
1.  按 F5 執行應用程式。 隨即會啟動 Excel，並會顯示含有 `bankAccounts` 中兩個帳戶資訊的資料表。 然後，會出現包含 Excel 資料表連結的 Word 文件。  
  
### <a name="to-clean-up-the-completed-project"></a>清除已完成的專案  
  
1.  在 Visual Studio 中，按一下 [建置]**** 功能表上的 [清除方案]****。 否則，每次在電腦上開啟 Excel 時，都會執行增益集。  
  
### <a name="to-find-the-pia-reference"></a>尋找 PIA 參考  
  
1.  重新執行應用程式，但不要按一下 [清除方案]****。  
  
2.  在 [開始]**** 功能表上，按一下 [所有程式]****。 接著，依序按一下 [Microsoft Visual Studio 2013]****、[Visual Studio Tools] ****和 [Visual Studio 命令提示字元 (2013)]****。  
  
3.  在 [Visual Studio 命令提示字元 (2013)] 視窗中鍵入 `ildasm`，然後按 ENTER 。 隨即會出現 IL DASM 視窗。  
  
4.  在 IL DASM 視窗的 [檔案]**** 功能表上，按一下 [開啟]****。 按兩下 [Visual Studio 2013]****，然後按兩下 [專案]****。 開啟您專案的資料夾，並查看 bin/Debug 資料夾中的 <您的專案名稱>**.dll。 按兩下 <您的專案名稱>**.dll。 新的視窗除了顯示會其他模組和組件的參考之外，還會顯示您專案的屬性。 請注意，組件中會包含命名空間 `Microsoft.Office.Interop.Excel` 和 `Microsoft.Office.Interop.Word`。 在 Visual Studio 2013 中，編譯器預設會將您所需要的類型從參考的 PIA 匯入組件。  
  
     如需詳細資訊，請參閱[如何：檢視組件內容](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709)。  
  
5.  按兩下**資訊清單**圖示。 隨即會出現一個視窗，內含專案所參考之項目的組件清單。 `Microsoft.Office.Interop.Excel` 和 `Microsoft.Office.Interop.Word` 未包含在清單中。 因為您專案所需的類型已匯入組件中，所以不需要 PIA 參考。 這會讓部署更為容易。 PIA 不需要存在於使用者的電腦上，而且因為應用程式不需要部署特定版本的 PIA，所以應用程式可以設計成與多個版本的 Office 搭配使用，但前提是所有版本都有必要的 API。  
  
     因為不再需要部署 PIA，所以您可以在使用多個版本 Office (包括舊版本) 的進階情況下，建立應用程式。 不過，這只適用於程式碼未使用供任何 API 時 (目前所用 Office 版本中不提供)。 您不一定清楚舊版本中是否有特定 API，也因為此，不建議使用舊版 Office。  
  
    > [!NOTE]
    >  在 Office 2003 之前，Office 未發行 PIA。 因此，產生 Office 2002 或舊版 Interop 組件唯一的方法，是匯入 COM 參考。  
  
6.  關閉資訊清單視窗和組件視窗。  
  
### <a name="to-restore-the-pia-dependency"></a>還原 PIA 相依性  
  
1.  在方案總管****中，按一下 [顯示所有檔案]**** 按鈕。 展開 [參考]**** 資料夾，然後選取 **Microsoft.Office.Interop.Excel**。 按 F4 顯示 [屬性]**** 視窗。  
  
2.  在 [屬性]**** 視窗中，將 [內嵌 Interop 類型]**** 屬性從 [True]**** 變更為 [False]****。  
  
3.  為 `Microsoft.Office.Interop.Word`，重複本程序中的步驟 1 和 2。  
  
4.  在 C# 中，將 `Autofit` 方法結尾的兩個 `DisplayInExcel` 呼叫標為註解。  
  
5.  按 F5 鍵，確認專案仍然正確地執行。  
  
6.  重複前一個程序中的步驟 1-3，開啟組件視窗。 請注意，`Microsoft.Office.Interop.Word` 和 `Microsoft.Office.Interop.Excel` 已不在內嵌的組件清單中。  
  
7.  按兩下**資訊清單**圖示，並捲動所參考之組件的清單。 `Microsoft.Office.Interop.Word` 和 `Microsoft.Office.Interop.Excel` 都在清單中。 由於應用程式會參考 Excel 和 Word PIA，而且 [內嵌 Interop 類型]**** 屬性設定為 [False]****，所以使用者電腦上必須具有這兩個組件。  
  
8.  在 Visual Studio 中，按一下 [建置]**** 功能表上的 [清除方案]****，清除已完成的專案。  
  
## <a name="see-also"></a>另請參閱  
 [自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [自動實作的屬性](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)   
 [集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [依位置和名稱傳遞引數](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)   
 [具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [如何：在 COM Interop 程式設計中使用已編製索引的屬性](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)   
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)   
 [逐步解說：從 Managed 組件內嵌類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [逐步解說：建立 Excel 的第一個 VSTO 增益集](http://msdn.microsoft.com/library/a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [互通性](../../../csharp/programming-guide/interop/index.md)
