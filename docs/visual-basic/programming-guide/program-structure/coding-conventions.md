---
title: Visual Basic 編碼慣例
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f73648888b28c349104a70e78c29eb208d438b78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761685"
---
# <a name="visual-basic-coding-conventions"></a>Visual Basic 編碼慣例
Microsoft 開發範例和文件，請遵循本主題中的指導方針。 如果您遵循相同的程式碼撰寫慣例，您可能會獲得下列好處：  
  
- 程式碼會有一致的外觀，讓讀者能夠更專注於未配置的內容。  
  
- 讀者了解您的程式碼更快速地因為它們會使先前的經驗為基礎的假設。  
  
- 您可以複製、 變更及更輕鬆地維護程式碼。  
  
- 您可以協助確保您的程式碼會示範 Visual Basic 的 「 最佳作法 」。  
  
## <a name="naming-conventions"></a>命名規範  
  
- 命名方針的相關資訊，請參閱[命名方針](../../../standard/design-guidelines/naming-guidelines.md)主題。  
  
- 請勿使用"My"my"做為變數名稱的一部分。 這種做法會建立與混淆`My`物件。  
  
- 您不必變更自動產生程式碼，使其符合方針中的物件名稱。  
  
## <a name="layout-conventions"></a>版面配置慣例  
  
- 插入定位點做為空格，並使用具有四個空格縮排的智慧縮排。  
  
- 使用**美化排列 （重新格式化） 的程式碼**重新格式化程式碼編輯器中的程式碼。 如需詳細資訊，請參閱 <<c0> [ 選項、 文字編輯器、 基本 (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。  
  
- 使用每一行只有一個陳述式。 請勿使用 Visual Basic 分隔符號字元 （:）。  
  
- 請避免使用明確行接續字元"_"而隱含行接續，在語言允許它。  
  
- 使用每一行只有一個宣告。  
  
- 如果**美化排列 （重新格式化） 的程式碼**不格式化接續行自動、 手動縮排接續行一個定位停駐點。 不過，永遠靠左對齊清單中的項目。  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- 加入方法和屬性定義之間的至少一個空白行。  
  
## <a name="commenting-conventions"></a>註解慣例  
  
- 將註解放到結尾的一行程式碼，而不是個別行上。  
  
- 開始以大寫字母，註解文字，並以句號結束註解文字。  
  
- 插入註解分隔符號 （'） 與註解文字之間的一個空格。  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- 請勿用格式化星號區塊註解。  
  
## <a name="program-structure"></a>程式結構  
  
- 當您使用`Main`方法，使用預設建構新的主控台應用程式，並使用`My`命令列引數。  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>語言指導方針  
  
### <a name="string-data-type"></a>String 資料類型  
  
- 若要串連字串，請使用連字號 (&)。  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
- 若要附加在迴圈中的字串，請使用<xref:System.Text.StringBuilder>物件。  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>寬鬆的委派事件處理常式  
 不要明確限定 （Object 和 EventArgs） 的引數至事件處理常式。 如果您未使用的事件引數傳遞至事件 (例如，sender as Object、 e as EventArgs)，使用寬鬆的委派，並省略事件引數，在您的程式碼：  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>不帶正負號的資料類型  
  
- 使用`Integer`而不是不帶正負號的類型，除非它們是必要。  
  
### <a name="arrays"></a>陣列  
  
- 當您初始化陣列的宣告行上時，請使用簡短的語法。 例如，使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     請勿使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- 在類型上，不是在變數上，請將陣列指示項。 例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     請勿使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- 當您宣告並初始化基本資料類型的陣列，請使用 {} 語法。 例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     請勿使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>使用 With 關鍵字  
 當您進行一系列的一個物件的呼叫時，請考慮使用`With`關鍵字：  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>使用 Try...Catch 和 Using 陳述式時使用 例外狀況處理  
 請勿使用 `On Error Goto`。  
  
### <a name="use-the-isnot-keyword"></a>使用 IsNot 關鍵字  
 使用`IsNot`關鍵字取代`Not...Is Nothing`。  
  
### <a name="new-keyword"></a>新的關鍵字  
  
- 使用簡短的具現化。 例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     前一行相當於這個：  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- 為新的物件，而不是無參數建構函式中使用物件初始設定式：  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>事件處理  
  
- 使用`Handles`而非`AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- 使用`AddressOf`，並執行不具現化委派明確：  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- 當您定義事件時，使用簡短的語法，並讓編譯器定義委派：  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- 不要驗證事件是否`Nothing`(null) 才能呼叫`RaiseEvent`方法。 `RaiseEvent` 檢查是否有`Nothing`引發事件之前。  
  
### <a name="using-shared-members"></a>使用共用的成員  
 呼叫`Shared`成員使用的類別名稱，不是從執行個體變數。  
  
### <a name="use-xml-literals"></a>使用 XML 常值  
 XML 常值來簡化您使用 （例如載入、 查詢及轉換） 的 XML 時所遇到的常見工作。 當您使用 XML 進行開發時，請遵循這些指導方針：  
  
- 您可以使用 XML 常值來建立 XML 文件和片段，而不要直接呼叫 XML Api。  
  
- 匯入 XML 命名空間，在檔案或專案層級，才能利用 XML 常值的效能最佳化。  
  
- 您可以使用 XML 軸屬性來存取 XML 文件中元素和屬性。  
  
- 使用內嵌的運算式，以加入值，並從現有的值，而不是使用 API 呼叫，例如建立 XML`Add`方法：  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>LINQ 查詢  
  
- 使用有意義的名稱，做為查詢變數：  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- 提供名稱的項目查詢中，以確定，匿名類型的屬性名稱大寫採用正確的 pascal 命名法大小寫：  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- 當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。 例如，如果您的查詢會傳回客戶名稱和訂單 ID，將其重新命名將它們保留為`Name`和`ID`結果：  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- 使用類型推斷查詢變數和範圍變數的宣告中：  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- 下對齊查詢子句`From`陳述式：  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- 使用`Where`子句在其他查詢子句，以便之後的查詢子句對篩選的資料集：  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- 使用`Join`子句來明確定義聯結作業，而不是使用`Where`子句隱含定義聯結作業：  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../../standard/security/secure-coding-guidelines.md)
