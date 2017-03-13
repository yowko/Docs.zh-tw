---
title: "Enum 陳述式 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Enum"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "列舉常數"
  - "Enum 陳述式"
  - "Private 關鍵字，Enum 陳述式"
  - "Enum 陳述式中的 public 關鍵字"
  - "變數 [Visual Basic] 列舉型別"
  - "列舉的常數"
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 44
---
# Enum 陳述式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

宣告列舉，並定義其成員的值。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>組件  
  
-   `attributelist`  
  
     選擇項。 這個列舉型別所套用的屬性清單。 您必須將 [屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md) 角括弧括住 ("`<`"和"`>`")。  
  
      <xref:System.FlagsAttribute> 屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員代表位元欄位中的列舉值。  
  
-   `accessmodifier`  
  
     選擇項。 指定哪些程式碼可以存取這個列舉型別。 可以是下列其中一項：  
  
    -   [公用](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [私用](../../../visual-basic/language-reference/modifiers/private.md)  
  
     您可以指定 `Protected``Friend` 以允許從列舉型別的類別，衍生的類別或相同的組件內的程式碼存取。  
  
-   `Shadows`  
  
     選擇項。 指定此列舉型別會重新宣告，並隱藏同名的程式設計項目或在基底類別中的多載項目集。 您可以指定 [陰影](../../../visual-basic/language-reference/modifiers/shadows.md) 只列舉型別本身，而非其任何成員。  
  
-   `enumerationname`  
  
     必要項。 列舉型別的名稱。 如需有效的名稱，請參閱 [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `datatype`  
  
     選擇項。 列舉型別及其所有成員的資料型別。  
  
-   `memberlist`  
  
     必要項。 此陳述式所宣告的成員常數的清單。 多個成員會出現在個別的原始程式碼行。  
  
     每個 `member` 具有以下的語法和組件︰ `[<attribute list>] member name [ = initializer ]`  
  
    |||  
    |-|-|  
    |組件|說明|  
    |`membername`|必要項。 這個成員的名稱。|  
    |`initializer`|選擇項。 在編譯時期評估，以及指派給這個成員的運算式。|  
  
-   `End` `Enum`  
  
     終止 `Enum` 區塊。  
  
## <a name="remarks"></a>備註  
 如果您有一組不會變更將彼此邏輯相關的值，您可以定義它們一起列舉型別。 這提供有意義的列舉型別和成員，也就是比它們的值更好記名稱。 然後，您可以使用在許多地方列舉型別成員在您的程式碼。  
  
 使用列舉的優點包括︰  
  
-   減少因調換或輸錯數字的錯誤。  
  
-   可讓您輕鬆地在未來變更的值。  
  
-   讓程式碼更方便閱讀，這表示它是比較不可能會導入錯誤。  
  
-   可確保往後相容性。 如果您使用列舉型別，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。  
  
 列舉型別具有名稱、 基礎的資料型別和成員集合。 每個成員代表一個常數。  
  
 類別、 結構、 模組或介面層級以外的任何程序，在宣告列舉類型是 *成員列舉*。 它是類別、 結構、 模組或介面宣告它的成員。  
  
 成員列舉型別可以從任何地方來存取其類別、 結構、 模組或介面中。 程式碼類別之外，結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。 您可以不需要使用完整限定的名稱加上 [匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 陳述式的原始程式檔。  
  
 命名空間層級以外任何類別、 結構、 模組或介面，在宣告列舉型別是命名空間中的成員。  
  
  *宣告內容* 列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，而且不能是程序。 如需詳細資訊，請參閱 [宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以分別套用在屬性列舉型別整體而言，但不是屬於其成員。 屬性會提供組件的中繼資料資訊。  
  
## <a name="data-type"></a>資料類型  
  `Enum` 陳述式可以宣告列舉的資料型別。 每個成員會在列舉資料類型。 您可以指定 `Byte`, ，`Integer`, ，`Long`, ，`SByte`, ，`Short`, ，`UInteger`, ，`ULong`, ，或 `UShort`。  
  
 如果您未指定 `datatype` 列舉，每個成員都會採用的資料型別其 `initializer`。 如果您同時指定 `datatype` 和 `initializer`, ，資料類型的 `initializer` 必須轉換成 `datatype`。 如果沒有 `datatype` 也 `initializer` 的話，資料類型的預設值為 `Integer`。  
  
## <a name="initializing-members"></a>初始化成員  
  `Enum` 陳述式可以初始化內容中選取之成員的 `memberlist`。 您使用 `initializer` 提供要指派給成員的運算式。  
  
 如果您未指定 `initializer` 成員時，Visual Basic 將它初始化為零 (如果是第一個 `member` 中 `memberlist`)，或值大一比前面 `member`。  
  
 提供在每個運算式 `initializer` 可以是常值、 其他已定義的常數和列舉型別成員已經定義，包括先前的這個列舉型別成員的任何組合。 您可以使用算術和邏輯運算子來結合這類項目。  
  
 您無法使用變數或函式中的 `initializer`。 不過，您可以使用轉換關鍵字例如 `CByte` 和 `CShort`。 您也可以使用 `AscW` 如果您呼叫與常數 `String` 或 `Char` 引數，因為可以在編譯時期評估的。  
  
 列舉型別不能有浮點值。 如果成員指派的浮點值和 `Option Strict` 設定為 on，就會發生編譯器錯誤。 如果 `Option Strict` 值會自動轉換為已關閉， `Enum` 型別。  
  
 如果成員的值超過允許的範圍為基礎的資料型別，或是初始化為基礎的資料類型所允許的最大值的任何成員，編譯器會報告錯誤。  
  
## <a name="modifiers"></a>修飾詞  
 類別、 結構、 模組和介面的成員列舉型別預設為公用存取。 您可以調整存取層級的存取修飾詞。 命名空間成員列舉型別預設為 friend 存取權限。 您可以調整為公開，但不是屬於私用或受保護的存取層。 如需詳細資訊，請參閱 [在 Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 所有列舉型別成員具有公用存取，且您無法使用任何存取修飾詞上面。 不過，如果列舉型別本身具有較嚴格的存取層級，指定列舉型別存取層級的優先順序。  
  
 根據預設，所有列舉型別是類型，其欄位是常數。 因此 `Shared`, ，`Static`, ，和 `ReadOnly` 宣告列舉型別或其成員時，就不能使用關鍵字。  
  
## <a name="assigning-multiple-values"></a>指派多個值  
 列舉型別通常代表互斥的值。 藉由 <xref:System.FlagsAttribute> 屬性中 `Enum` 宣告中，您可以改為指派多個值給列舉型別的執行個體。  <xref:System.FlagsAttribute> 屬性會指定列舉型別視為位元欄位，也就是一組旗標。 這些稱為 *位元* 列舉型別。  
  
 當您宣告列舉型別使用 <xref:System.FlagsAttribute> 屬性，我們建議您使用是 2、 1、 2、 4、 8、 16 和等等的次方值。 我們也建議 「 無 」 成員，其值為 0 的名稱。 如需其他指導方針，請參閱 <xref:System.FlagsAttribute> 和 <xref:System.Enum>。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `Enum` 陳述式。 請注意，成員指 `EggSizeEnum.Medium`, ，而不是 `Medium`。  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例中的方法已超出 `Egg` 類別。 因此， `EggSizeEnum` 完整限定為 `Egg.EggSizeEnum`。  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用 `Enum` 陳述式來定義一組相關的具名常數的值。 在此情況下，值會是您可以選擇設計資料庫的資料輸入表單的色彩。  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例包含正數和負數的值。  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中， `As` 子句用來指定 `datatype` 的列舉型別。  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用位元的列舉型別。 多個值可以指派給位元的列舉型別的執行個體。  `Enum` 宣告包含 <xref:System.FlagsAttribute> 屬性，表示列舉型別可以視為一組旗標。  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>範例  
 下列範例會逐一列舉型別。 它會使用 <xref:System.Enum.GetNames%2A> 方法來擷取列舉中的成員名稱的陣列和 <xref:System.Enum.GetValues%2A> 擷取成員值的陣列。  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Enum>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [常數和列舉型別](../../../visual-basic/language-reference/constants-and-enumerations.md)