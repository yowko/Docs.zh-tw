---
title: HOW TO：在 Office 程式設計中使用具名引數和選用引數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 90b60a6410ffbe7f9802b01bf3303b6e842a1424
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002797"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>HOW TO：在 Office 程式設計中使用具名引數和選用引數 (C# 程式設計指南)

C# 4 中引進的具名引數和選擇性引數，可加強 C# 程式設計的便利性、彈性和可讀性。 此外，這些功能還可大幅加速對 COM 介面 (例如 Microsoft Office Automation API) 的存取。

在下列範例中，[ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) 方法有十六個參數，這些參數代表資料表的特性，例如欄數和列數、格式、邊框、字型和顏色。 所有十六個參數都是選擇性的，因為大多時候您不會想要為所有參數指定特定值。 不過，如果不使用具名和選擇性引數，則必須為每個參數提供值或預留位置值。 如果使用具名和選擇性引數，就只會為專案所需的參數指定值。

您必須已在電腦上安裝 Microsoft Office Word，才能完成這些程序。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>建立新的主控台應用程式

1. 啟動 Visual Studio。

2. 在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。

3. 在 [範本類別] 窗格中，展開 [Visual C#]，然後按一下 [Windows]。

4. 查看 [範本] 窗格頂端，確定 [.NET Framework 4] 出現在 [目標 Framework] 方塊中。

5. 按一下 [範本] 窗格中的 [主控台應用程式]。

6. 在 [名稱] 欄位中鍵入專案的名稱。

7. 按一下 [確定]。

     新的專案隨即會出現在**方案總管**中。

## <a name="to-add-a-reference"></a>若要加入參考

1. 在**方案總管**中，以滑鼠右鍵按一下您的專案名稱，然後按一下 [加入參考]。 [加入參考] 對話方塊隨即出現。

2. 在 [.NET] 頁面上，選取 [元件名稱] 清單中的 [Microsoft.Office.Interop.Word]。

3. 按一下 [確定]。

## <a name="to-add-necessary-using-directives"></a>加入必要的 using 指示詞

1. 在方案總管中，以滑鼠右鍵按一下 *Program.cs* 檔案，然後按一下 [檢視程式碼]。

2. 將下列 `using` 指示詞新增至程式碼檔案的頂端：

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>在 Word 文件中顯示文字

1. 在*Program.cs*的 `Program` 類別中，新增下列方法來建立 word 應用程式和 word 檔。 [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) 方法有四個選擇性參數。 此範例會使用其預設值。 因此，呼叫陳述式中不需要引數。

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. 在方法的結尾新增下列程式碼，以定義要在檔中顯示文字的位置，以及要顯示的文字：

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>若要執行應用程式

1. 將下列語句加入 Main：

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. 按<kbd>CTRL</kbd>+<kbd>F5</kbd>來執行專案。 隨即會出現含有指定文字的 Word 文件。

## <a name="to-change-the-text-to-a-table"></a>將文字變更為表格
  
1. 使用 `ConvertToTable` 方法將文字放在表格中。 此方法有十六個選擇性參數。 IntelliSense 會以方括號括住選擇性參數，如下圖所示。

     ![ConvertToTable 方法的參數清單](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     具名和選擇性引數可讓您只針對要變更的參數指定值。 將下列程式碼新增至 `DisplayInWord` 方法的結尾，以建立簡單的表格。 此引數會指定以 `range` 內文字字串中的逗號來分隔表格的儲存格。

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     在舊版中C#，對 `ConvertToTable` 的呼叫需要每個參數都有參考引數，如下列程式碼所示：
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. 按<kbd>CTRL</kbd>+<kbd>F5</kbd>來執行專案。

## <a name="to-experiment-with-other-parameters"></a>試驗其他參數

1. 若要變更資料表，使其具有一個資料行和三個數據列，請將 `DisplayInWord` 中的最後一行取代為下列語句，然後輸入<kbd>CTRL</kbd>+<kbd>F5</kbd>。  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. 若要為數據表指定預先定義的格式，請將 `DisplayInWord` 中的最後一行取代為下列語句，然後輸入<kbd>CTRL</kbd>+<kbd>F5</kbd>。 此格式可以是任何 [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) 常數。

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>範例

下列程式碼包含完整的範例：

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>另請參閱

- [具名和選擇性引數](./named-and-optional-arguments.md)
