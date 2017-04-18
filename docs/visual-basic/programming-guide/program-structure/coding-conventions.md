---
title: "Visual Basic 編碼慣例 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5712f14d53b86552a0b82af38ecf579577ef3fa1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-coding-conventions"></a>Visual Basic 編碼慣例
Microsoft 開發範例和文件，請遵循本主題中的指導方針。 如果您遵循相同的程式碼撰寫慣例，您可能會獲得下列好處︰  
  
-   您的程式碼將會有一致的外觀，讓讀者能夠更專注於內容，而非版面配置。  
  
-   讀者了解您的程式碼更快速地因為它們會使先前的經驗為基礎的假設。  
  
-   您可以複製、 變更及維護程式碼更容易。  
  
-   您可以協助確保您的程式碼會示範 Visual Basic 的 「 最佳作法 」。  
  
## <a name="naming-conventions"></a>命名規範  
  
-   命名方針的相關資訊，請參閱[命名方針](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)主題。  
  
-   請勿使用 「 我的 」 或 「 我的 」 做為變數名稱的一部分。 這種作法建立混淆在一起`My`物件。  
  
-   您不必變更中自動產生的程式碼使其符合準則的物件名稱。  
  
## <a name="layout-conventions"></a>版面配置慣例  
  
-   插入空格 索引標籤，並使用四個空間縮排與智慧型縮排。  
  
-   使用**美化 （重新格式化） 的程式碼**重新格式化程式碼編輯器中的程式碼。 如需詳細資訊，請參閱[基本文字編輯器、 選項 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic)。  
  
-   使用每行只有一個陳述式。 請勿使用 Visual Basic 的行分隔符號字元 （:）。  
  
-   請避免使用明確的行接續字元"_"有利於隱含行接續符號，只要該語言可以讓它。  
  
-   使用每行只有一個宣告。  
  
-   如果**美化 （重新格式化） 的程式碼**不接續線格式自動、 手動縮排接續行一個定位點。 不過，一定左對齊 清單中的項目。  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   新增方法與屬性定義之間的至少一個空白行。  
  
## <a name="commenting-conventions"></a>註解慣例  
  
-   將註解放到結尾的一行程式碼，而不是個別行上。  
  
-   開始以大寫字母，註解文字，並以句號結束註解文字。  
  
-   插入註解分隔符號 （'） 與註解文字之間的一個空格。  
  
     [!code-vb[VbVbalrGuidelines #&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   請勿用格式化的星號區塊註解。  
  
## <a name="program-structure"></a>程式結構  
  
-   當您使用`Main`方法，使用預設建構新的主控台應用程式，並使用`My`命令列引數。  
  
     [!code-vb[VbVbalrGuidelines #&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>語言指導方針  
  
### <a name="string-data-type"></a>String 資料類型  
  
-   若要串連的字串，使用連字號 （&）。  
  
     [!code-vb[VbVbalrGuidelines #&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   若要附加在迴圈中的字串，請使用<xref:System.Text.StringBuilder>物件。</xref:System.Text.StringBuilder>  
  
     [!code-vb[VbVbalrGuidelines #&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>寬鬆的委派事件處理常式中  
 請勿明確限定 （物件和 EventArgs） 的引數至事件處理常式。 如果您未使用的事件引數傳遞至事件 （例如，寄件者物件，e EventArgs），使用比較不嚴謹的委派，並排除您的程式碼中的事件引數︰  
  
 [!code-vb[VbVbalrGuidelines #&7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>不帶正負號的資料類型  
  
-   使用`Integer`而不是不帶正負號的型別，除非它們所需的位置。  
  
### <a name="arrays"></a>陣列  
  
-   當您在宣告行上初始化陣列時，請使用簡短的語法。 例如，使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines #&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     請勿使用下列語法。  
  
     [!code-vb[VbVbalrGuidelines #&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   變數型別，而非將陣列指示項。 例如，使用下列語法︰  
  
     [!code-vb[VbVbalrGuidelines #&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     請勿使用下列語法︰  
  
     [!code-vb[VbVbalrGuidelines #&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   宣告和初始化陣列的基本資料型別時，請使用 {} 語法。 例如，使用下列語法︰  
  
     [!code-vb[VbVbalrGuidelines #&12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     請勿使用下列語法︰  
  
     [!code-vb[VbVbalrGuidelines #&13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>使用 With 關鍵字  
 當您進行一系列的一個物件的呼叫時，請考慮使用`With`關鍵字︰  
  
 [!code-vb[VbVbalrGuidelines #&15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>使用 Try …Catch 和 Using 陳述式時使用 例外狀況處理  
 請勿使用`On Error Goto`。  
  
### <a name="use-the-isnot-keyword"></a>使用 IsNot 關鍵字  
 使用`IsNot`關鍵字取代`Not...Is Nothing`。  
  
### <a name="new-keyword"></a>New 關鍵字  
  
-   使用簡短的具現化。 例如，使用下列語法︰  
  
     [!code-vb[VbVbalrGuidelines #&21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     前一行相當於這個︰  
  
     [!code-vb[VbVbalrGuidelines #&22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   為新的物件，而不是無參數建構函式中使用物件初始設定式︰  
  
     [!code-vb[VbVbalrGuidelines #&23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>事件處理  
  
-   使用`Handles`而不是`AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines #&24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   使用`AddressOf`，並不明確產生的委派︰  
  
     [!code-vb[VbVbalrGuidelines #&25;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   當您定義的事件時，使用簡短的語法，並讓編譯器定義委派︰  
  
     [!code-vb[VbVbalrGuidelines #&26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   不會驗證事件是否`Nothing`(null) 才能呼叫`RaiseEvent`方法。 `RaiseEvent`檢查是否有`Nothing`引發事件之前。  
  
### <a name="using-shared-members"></a>使用共用的成員  
 呼叫`Shared`成員使用的類別名稱，不能從執行個體變數。  
  
### <a name="use-xml-literals"></a>使用 XML 常值  
 XML 常值來簡化處理 （例如載入、 查詢和轉換） 的 XML 時遇到的常見工作。 當您開發 xml 時，請遵循下列方針︰  
  
-   您可以使用 XML 常值來建立 XML 文件和片段，而不是直接呼叫 XML Api。  
  
-   匯入 XML 命名空間，在檔案或專案層級，若要利用 XML 常值的效能最佳化。  
  
-   您可以使用 XML 軸屬性來存取 XML 文件中元素和屬性。  
  
-   使用內嵌的運算式包含值，並從現有的值，而不是使用 API 呼叫，例如建立 XML`Add`方法︰  
  
     [!code-vb[VbVbalrGuidelines #&27;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>LINQ 查詢  
  
-   使用有意義的名稱，請為查詢變數︰  
  
     [!code-vb[VbVbalrGuidelines #&28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   提供的查詢，以確定，匿名型別的屬性名稱大寫正確使用 pascal 命名法中的項目名稱大小寫︰  
  
     [!code-vb[VbVbalrGuidelines #&29;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   當結果中的屬性名稱可能會造成混淆時，請重新命名屬性。 例如，如果您的查詢傳回了客戶名稱和訂單 ID，重新命名並不是保留為`Name`和`ID`結果︰  
  
     [!code-vb[VbVbalrGuidelines #&30;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   查詢變數和範圍變數的宣告中使用型別推斷︰  
  
     [!code-vb[VbVbalrGuidelines #&31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   對齊查詢子句下,`From`陳述式︰  
  
     [!code-vb[VbVbalrGuidelines #&32;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   使用`Where`子句之前其他查詢子句，以便之後的查詢子句對篩選的資料集︰  
  
     [!code-vb[VbVbalrGuidelines #&33;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   使用`Join`子句來明確定義的聯結作業，而不是使用`Where`子句來隱含定義的聯結作業︰  
  
     [!code-vb[VbVbalrGuidelines #&34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [安全程式碼撰寫方針](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
