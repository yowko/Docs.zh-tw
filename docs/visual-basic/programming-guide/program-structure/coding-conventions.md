---
title: Visual Basic 編碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: 580a6e1caa78ea981b6d2be68a6e7c61e2ad55d7
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433816"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic 編碼慣例
Microsoft 會依照本主題中的指導方針來開發範例和檔。 如果您遵循相同的編碼慣例, 您可能會獲得下列優點:  
  
- 您的程式碼會有一致的外觀, 讓讀者可以更專注于內容, 而不是版面配置。  
  
- 讀者會更快速地瞭解您的程式碼, 因為它們可以根據先前的經驗做出假設。  
  
- 您可以更輕鬆地複製、變更及維護程式碼。  
  
- 您可以協助確保您的程式碼會針對 Visual Basic 示範「最佳做法」。  
  
## <a name="naming-conventions"></a>命名規範  
  
- 如需命名指導方針的詳細資訊, 請參閱[命名指導方針](../../../standard/design-guidelines/naming-guidelines.md)主題。  
  
- 請勿使用 "My" 或 "my" 作為變數名稱的一部分。 這種作法會與`My`物件產生混淆。  
  
- 您不需要在自動產生的程式碼中變更物件的名稱, 使其符合方針。  
  
## <a name="layout-conventions"></a>版面配置慣例  
  
- 將索引標籤插入空格, 並使用具有四個空格縮排的智慧型縮排。  
  
- 使用程式**代碼的整齊清單 (重新格式化)** , 在程式碼編輯器中重新格式化您的程式碼。 如需詳細資訊, 請參閱[選項、文字編輯器、基本 (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。  
  
- 每行只能使用一個語句。 請勿使用 Visual Basic 行分隔字元 (:)。  
  
- 請避免使用明確行接續字元 "_", 以在語言允許的地方隱含行接續。  
  
- 每行只能使用一個宣告。  
  
- 如果程式**代碼的整齊清單 (重新格式化)** 不會自動格式化接續行, 請手動將接續行縮排一次定位停駐點。 不過, 一律會靠左對齊清單中的專案。  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- 在方法和屬性定義之間新增至少一個空白行。  
  
## <a name="commenting-conventions"></a>註解慣例  
  
- 將批註放在另一行, 而不是一行程式碼的結尾。  
  
- 以大寫字母開始註解文字, 並以句點結束註解文字。  
  
- 在批註分隔符號 (') 和註解文字之間插入一個空格。  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- 不要以星號的格式化區塊來括住批註。  
  
## <a name="program-structure"></a>程式結構  
  
- 當您使用`Main`方法時, 請使用新的主控台應用程式的預設結構, `My`並使用做為命令列引數。  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>語言指導方針  
  
### <a name="string-data-type"></a>String 資料類型  
  
- 使用[字串內插補點](https://docs.microsoft.com/dotnet/visual-basic/programming-guide/language-features/strings/interpolated-strings)串連短字串，如下列程式碼所示。
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- 若要在迴圈中附加字串, <xref:System.Text.StringBuilder>請使用物件。  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>事件處理常式中的寬鬆委派  
 請勿將引數 (物件和 EventArgs) 明確限定為事件處理常式。 如果您不是使用傳遞至事件的事件引數 (例如, 傳送者作為物件, e as EventArgs), 請使用寬鬆的委派, 並在您的程式碼中省略事件引數:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>不帶正負號的資料類型  
  
- 使用`Integer` , 而不是不帶正負號的類型, 但必要的位置除外。  
  
### <a name="arrays"></a>陣列  
  
- 當您在宣告行上初始化陣列時, 請使用簡短的語法。 例如, 使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     請勿使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- 將陣列指示項放在型別上, 而不是在變數上。 例如, 使用下列語法:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     請勿使用下列語法:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- 當您宣告並初始化基本資料類型的陣列時, 請使用 {} 語法。 例如, 使用下列語法:  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     請勿使用下列語法:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>使用 With 關鍵字  
 當您對一個物件進行一系列的呼叫時, 請考慮`With`使用關鍵字:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>使用 [嘗試 ...]使用例外狀況處理時的 Catch 和 Using 語句  
 請勿使用 `On Error Goto`。  
  
### <a name="use-the-isnot-keyword"></a>使用 IsNot 關鍵字  
 請使用`IsNot`關鍵字, `Not...Is Nothing`而不是。  
  
### <a name="new-keyword"></a>New 關鍵字  
  
- 使用簡短的具現化。 例如, 使用下列語法:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     上一行相當於:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- 針對新物件使用物件初始化運算式, 而不是無參數的函式:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>事件處理  
  
- 使用`Handles` ,`AddHandler`而不是:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- 使用`AddressOf`, 而且不明確地具現化委派:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- 當您定義事件時, 請使用簡短語法, 並讓編譯器定義委派:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- `Nothing` 在`RaiseEvent`呼叫方法之前, 請不要驗證事件是否為 (null)。 `RaiseEvent`在引發`Nothing`事件之前, 檢查是否有。  
  
### <a name="using-shared-members"></a>使用共用成員  
 使用`Shared`類別名稱呼叫成員, 而不是從執行個體變數。  
  
### <a name="use-xml-literals"></a>使用 XML 常值  
 XML 常值可簡化您在使用 XML 時所遇到的最常見工作 (例如, 載入、查詢和轉換)。 當您使用 XML 進行開發時, 請遵循下列指導方針:  
  
- 使用 XML 常值來建立 XML 檔和片段, 而不是直接呼叫 XML Api。  
  
- 匯入檔案或專案層級的 XML 命名空間, 以利用 XML 常值的效能優化。  
  
- 使用 XML 軸屬性來存取 XML 檔中的元素和屬性。  
  
- 使用內嵌運算式來包含值, 並從現有的值建立 XML, 而不是使用 API 呼叫`Add` , 例如方法:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>LINQ 查詢  
  
- 針對查詢變數使用有意義的名稱:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- 在查詢中提供元素的名稱, 以確定匿名型別的屬性名稱使用 Pascal 大小寫正確地大寫:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- 當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。 例如, 如果您的查詢傳回客戶名稱和訂單識別碼, 請將其重新命名, 而不要在`Name`結果`ID`中將它們保留為和:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- 在查詢變數和範圍變數的宣告中使用類型推斷:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- 在`From`語句底下對齊查詢子句:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- 在`Where`其他查詢子句之前使用子句, 讓稍後的查詢子句在篩選的資料集上運作:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- 使用子句來明確定義聯結作業, 而不是`Where`使用子句來隱含定義聯結運算: `Join`  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)
