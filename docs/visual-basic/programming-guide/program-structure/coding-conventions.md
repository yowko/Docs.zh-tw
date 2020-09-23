---
title: 編碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: eae283c757ddeb1290c15d82a41c8028a8941e63
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059154"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic 編碼慣例

Microsoft 會依照本主題中的指導方針來開發範例與檔。 如果您遵循相同的程式碼撰寫慣例，您可能會獲得下列優點：  
  
- 您的程式碼會有一致的外觀，讓讀者可以更專注于內容，而不是版面配置。  
  
- 讀者可以更快速地瞭解您的程式碼，因為它們可以根據先前的經驗進行假設。  
  
- 您可以更輕鬆地複製、變更和維護程式碼。  
  
- 您可以協助確保您的程式碼會示範 Visual Basic 的「最佳作法」。  
  
## <a name="naming-conventions"></a>命名規範  
  
- 如需命名方針的詳細資訊，請參閱 [命名指導方針](../../../standard/design-guidelines/naming-guidelines.md) 主題。  
  
- 請勿使用 "My" 或 "my" 作為變數名稱的一部分。 這種作法會與物件產生混淆 `My` 。  
  
- 您不需要在自動產生的程式碼中變更物件的名稱，使其符合指導方針。  
  
## <a name="layout-conventions"></a>版面配置慣例  
  
- 以空格插入索引標籤，並使用具有四個空格縮排的智慧縮排。  
  
- 使用 **整齊的清單 (重新格式化程式碼) ** ，以在程式碼編輯器中重新格式化您的程式碼。 如需詳細資訊，請參閱 [ [選項]、[文字編輯器]、[基本 (Visual Basic) ](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。  
  
- 每行只能使用一個語句。 請勿使用 Visual Basic 行分隔字元 (： ) 。  
  
- 在語言允許的任何地方，請避免使用明確的行接續字元 "_" 來取代隱含行接續。  
  
- 每行只能使用一個宣告。  
  
- 如果有很多 **的 (重新格式化) 的程式碼** 並不會自動將接續行格式化，請以手動方式將接續行縮排一次 不過，一律會將清單中的專案靠左對齊。  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- 在方法與屬性定義之間加入至少一個空白行。  
  
## <a name="commenting-conventions"></a>註解慣例  
  
- 將批註放在不同的行，而不是程式程式碼的結尾。  
  
- 使用大寫字母來開始註解文字，並以句點結束註解文字。  
  
- 在批註分隔符號 ( ' ) 和註解文字之間插入一個空格。  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- 請勿以星號的格式化區塊括住批註。  
  
## <a name="program-structure"></a>程式結構  
  
- 當您使用 `Main` 方法時，請使用新的主控台應用程式的預設結構，並使用做 `My` 為命令列引數。  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>語言指導方針  
  
### <a name="string-data-type"></a>String 資料類型  
  
- 使用[字串內插補點](../language-features/strings/interpolated-strings.md)串連短字串，如下列程式碼所示。
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- 若要在迴圈中附加字串，請使用 <xref:System.Text.StringBuilder> 物件。  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>事件處理常式中寬鬆的委派  

 請勿明確限定引數 (物件和 EventArgs) 至事件處理常式。 如果您不是使用傳遞至事件的事件引數 (例如，傳送者為物件、e 表示 EventArgs) ，請使用寬鬆的委派，並在程式碼中省略事件引數：  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>不帶正負號的資料類型  
  
- 使用 `Integer` 而非不帶正負號的類型，但不含符號類型。  
  
### <a name="arrays"></a>陣列  
  
- 當您在宣告行上初始化陣列時，請使用簡短的語法。 例如，請使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     請勿使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- 將陣列指示項放在型別上，而不是變數上。 例如，請使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     請勿使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- 當您宣告並初始化基本資料類型的陣列時，請使用 {} 語法。 例如，請使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     請勿使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>使用 With 關鍵字  

 當您對一個物件進行一連串的呼叫時，請考慮使用 `With` 關鍵字：  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>使用 Try .。。當您使用例外狀況處理時的 Catch 和 Using 語句  

 請勿使用 `On Error Goto`。  
  
### <a name="use-the-isnot-keyword"></a>使用 IsNot 關鍵字  

 使用 `IsNot` 關鍵字而不是 `Not...Is Nothing` 。  
  
### <a name="new-keyword"></a>New 關鍵字  
  
- 使用簡短具現化。 例如，請使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     上述程式程式碼相當於：  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- 針對新物件使用物件初始化運算式，而不是無參數的函式：  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>事件處理  
  
- 使用 `Handles` 而不是 `AddHandler` ：  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- 使用 `AddressOf` ，而且不要明確地具現化委派：  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- 當您定義事件時，請使用簡短語法，然後讓編譯器定義委派：  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- `Nothing`在呼叫方法之前，請不要確認事件是否 (null) `RaiseEvent` 。 `RaiseEvent``Nothing`在引發事件之前檢查。  
  
### <a name="using-shared-members"></a>使用共用成員  

 `Shared`使用類別名稱呼叫成員，而不是從執行個體變數。  
  
### <a name="use-xml-literals"></a>使用 XML 常值  

 XML 常值會簡化您使用 XML (時所遇到的最常見工作，例如載入、查詢和轉換) 。 當您使用 XML 進行開發時，請遵循下列指導方針：  
  
- 使用 XML 常值來建立 XML 檔和片段，而不是直接呼叫 XML Api。  
  
- 匯入檔案或專案層級的 XML 命名空間，以利用 XML 常值的效能優化。  
  
- 使用 XML 軸屬性來存取 XML 檔中的元素和屬性。  
  
- 使用內嵌運算式來包含值，並從現有的值建立 XML，而不使用 API 呼叫（例如 `Add` 方法）：  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>LINQ 查詢  
  
- 針對查詢變數使用有意義的名稱：  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- 提供查詢中專案的名稱，以確保匿名型別的屬性名稱使用 Pascal 大小寫正確地大寫：  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- 當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。 例如，如果您的查詢傳回客戶名稱和訂單識別碼，請將其重新命名，而不是 `Name` `ID` 在結果中保留它們：  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- 在查詢變數和範圍變數的宣告中使用類型推斷：  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- 在語句下對齊查詢子句 `From` ：  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- 在 `Where` 其他查詢子句之前使用子句，以便稍後的查詢子句在篩選過的資料集上運作：  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- 使用 `Join` 子句來明確定義聯結作業，而不是使用 `Where` 子句來隱含地定義聯結操作：  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)
