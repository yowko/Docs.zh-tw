---
title: "Visual Basic Coding Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "coding conventions, Visual Basic"
  - "examples [Visual Basic], coding conventions"
  - "Visual Basic code, conventions"
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 48
---
# Visual Basic Coding Conventions
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Microsoft 會遵循本主題中的方針來開發範例和文件。  如果您遵循相同的編碼慣例，則可能獲得下列優點：  
  
-   程式碼會有一致的外觀，以便讀取器 \(Reader\) 可以更容易將焦點放在內容，而非配置。  
  
-   讀取器能夠更迅速地理解您的程式碼，因為可依據先前的經驗進行假設。  
  
-   您可以更輕鬆地複製，變更及維護程式碼。  
  
-   您可以協助確保您的程式碼會表現出 Visual Basic 的最佳做法。  
  
## 命名規範  
  
-   如需命名方針的詳細資訊，請參閱[命名方針](../Topic/Naming%20Guidelines.md)主題。  
  
-   請不要使用 "My" 或 "my" 做為變數名稱的一部分。  此做法會與 `My` 物件產生混淆。  
  
-   您不必在自動產生的程式碼中變更物件名稱，也可以使其符合方針。  
  
## 配置慣例  
  
-   插入定位點做為空格，並使用四個空格縮排的智慧縮排。  
  
-   使用 \[**程式碼美化排列 \(重新格式化\)**\]，重新格式化程式碼編輯器中的程式碼。  如需詳細資訊，請參閱[基本 \(Visual Basic\)、文字編輯器、選項](/visual-studio/ide/reference/options-text-editor-basic-visual-basic)。  
  
-   每行只使用一個陳述式。  不要使用 Visual Basic 分隔符號字元 \(:\)。  
  
-   避免使用明確行接續字元 "\_"，而應在語言允許的情況下，使用隱含行接續符號。  
  
-   每行只使用一個宣告。  
  
-   如果 \[**程式碼美化排列 \(重新格式化\)**\] 不會自動格式化接續行，請手動將接續行縮排一個定位停駐點。  不過，永遠靠左對齊清單中的項目。  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   在方法與屬性定義之間加入至少一個空白行。  
  
## 註解慣例  
  
-   將註解放到另一行，不要放在程式碼行的結尾。  
  
-   註解文字開頭為大寫字母，註解文字結尾為句點。  
  
-   在註解分隔符號 \('\) 與註解文字之間插入一個空格。  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#2)]  
  
-   不要用格式化星號區塊來包圍註解。  
  
## 程式結構  
  
-   在使用 `Main` 方法時，請對新的主控台應用程式 \(Console Application\) 使用預設建構，並對命令列引數使用 `My`。  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#3)]  
  
## 語言方針  
  
### 字串資料類型  
  
-   若要串連字串，請使用連字號 \(&\)。  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#4)]  
  
-   若要在迴圈中附加字串，請使用 <xref:System.Text.StringBuilder> 物件。  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#5)]  
  
### 事件處理常式中比較不嚴謹的委派  
 不要明確限定事件處理常式的引數 \(Object 和 EventArgs\)。  如果您不使用傳遞給事件的事件引數 \(例如，sender as Object、e as EventArgs\)，請使用寬鬆委派，並在程式碼中省略事件引數：  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#7)]  
  
### 不帶正負號的資料類型  
  
-   使用 `Integer` 而不是不帶正負號的類型，除非需要後者。  
  
### 陣列  
  
-   在宣告行上初始化陣列時，請使用簡短的語法。  例如，使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#8)]  
  
     不要使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#9)]  
  
-   將陣列指示項放在類型上，不要放在變數上：  例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#11)]  
  
     不要使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#10)]  
  
-   當您宣告及初始化基本資料類型的陣列時，使用 { } 語法。  例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#12)]  
  
     不要使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#13)]  
  
### 使用 With 關鍵字  
 對一個物件使用一連串的呼叫時，請考慮使用 `With` 關鍵字：  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#15)]  
  
### 使用例外狀況處理時使用 Try...Catch 和 Using 陳述式  
 不要使用 `On Error Goto`。  
  
### 使用 IsNot 關鍵字  
 使用 `IsNot` 關鍵字取代 `Not...Is Nothing`.  
  
### New 關鍵字  
  
-   使用短的執行個體化。  例如，使用下列語法：  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#21)]  
  
     前一行等於：  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#22)]  
  
-   為新物件使用物件初始設定式，代替無參數的建構函式 \(Constructor\)：  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#23)]  
  
### 事件處理  
  
-   使用 `Handles`，而非 `AddHandler`：  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#24)]  
  
-   使用 `AddressOf`，且不要明確地對委派 \(Delegate\) 執行個體化。  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#25)]  
  
-   當您定義事件時，請使用短語法並且讓編譯器定義委派：  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#26)]  
  
-   在呼叫 `RaiseEvent` 方法之前，不要驗證事件是否為 `Nothing` \(null\)。  `RaiseEvent` 會在引發事件之前檢查 `Nothing`。  
  
### 使用共用成員  
 使用類別名稱呼叫 `Shared` 成員，而不要從執行個體變數進行呼叫。  
  
### 使用 XML 常值  
 XML 常值 \(Literal\) 會簡化在您使用 XML 時所遇到的最常見工作 \(例如載入、查詢和轉換\)。  當您以 XML 進行開發時，請遵循下列方針：  
  
-   使用 XML 常值建立 XML 文件和片段，而不要直接呼叫 XML API。  
  
-   在檔案或專案等級匯入 XML 命名空間，以充分利用 XML 常值的效能最佳化。  
  
-   使用 XML 軸屬性 \(Property\) 存取 XML 文件中的項目和屬性 \(Attribute\)。  
  
-   使用內嵌運算式，以加入值並從現有值建立 XML，而不要使用如 `Add` 方法之類的 API 呼叫：  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#27)]  
  
### LINQ 查詢  
  
-   使用有意義的名稱做為查詢變數的名稱：  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#28)]  
  
-   提供查詢中項目的名稱，確保匿名類型的屬性名稱大寫採用正確的 Pascal 大小寫：  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#29)]  
  
-   當結果中的屬性名稱會變成模稜兩可時，請重新命名屬性。  例如，如果您的查詢傳回客戶名稱和訂單 ID，請不要保留為結果中的 `Name` 和 `ID`，而要加以重新命名：  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#30)]  
  
-   在查詢變數和範圍變數的宣告中使用類型推斷：  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#31)]  
  
-   將查詢子句對齊在 `From` 陳述式下方：  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#32)]  
  
-   將 `Where` 子句使用在其他查詢子句之前，以確保後來的查詢子句會在已縮減且篩選過的資料集上運作：  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#33)]  
  
-   使用 `Join` 子句明確定義聯結 \(Join\) 作業，而不要使用 `Where` 子句隱含定義聯結作業：  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/visualbasic/VBProject/Class1.vb#34)]  
  
## 請參閱  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)