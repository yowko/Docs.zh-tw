---
title: Enum 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="enum-statement-visual-basic"></a>Enum 陳述式 (Visual Basic)
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
  
     選擇性。 套用至此列舉的屬性清單。 您必須將[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)在角括號 ("`<`"和"`>`")。  
  
     <xref:System.FlagsAttribute>屬性表示列舉型別的執行個體的值可以包含多個列舉成員，而且每個成員代表位元欄位中的列舉值。  
  
-   `accessmodifier`  
  
     選擇性。 指定哪些程式碼可以存取這個列舉型別。 可以是下列其中一項：  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Protected 的 Friend](../../language-reference/modifiers/protected-friend.md)
    
    - [受保護的私用](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     選擇性。 指定此列舉型別會重新宣告並隱藏相同具名的程式設計項目或基底類別中的多載項目集。 您可以指定[陰影](../../../visual-basic/language-reference/modifiers/shadows.md)只列舉型別本身，而非它的任何成員。  
  
-   `enumerationname`  
  
     必要。 列舉型別的名稱。 如需有效的名稱資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `datatype`  
  
     選擇性。 資料類型的列舉型別及其所有成員。  
  
-   `memberlist`  
  
     必要。 此陳述式所宣告的成員常數的清單。 多個成員會出現在個別的原始程式碼行。  
  
     每個`member`具有下列語法和組件： `[<attribute list>] member name [ = initializer ]`  
  
    |組件|描述|  
    |---|---|  
    |`membername`|必要。 這個成員的名稱。|  
    |`initializer`|選擇性。 在編譯時期評估，以及指派給這個成員的運算式。|  
  
-   `End` `Enum`  
  
     終止 `Enum` 區塊。  
  
## <a name="remarks"></a>備註  
 如果您有一組邏輯上彼此相關的不變值時，您可以定義它們一起列舉型別。 這提供有意義的名稱，列舉型別和成員，也就是您更輕鬆地記住比它們的值。 然後，您可以使用在許多地方列舉型別成員在您的程式碼中。  
  
 使用列舉的優點包括：  
  
-   減少調換或輸入數字的錯誤所造成的錯誤。  
  
-   可讓您輕鬆地在未來變更的值。  
  
-   讓程式碼更方便閱讀，這表示它是比較不可能會導入錯誤。  
  
-   可確保往後相容性。 如果您使用列舉型別時，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。  
  
 列舉型別具有名稱、 基礎的資料型別和成員集合。 每個成員表示常數。  
  
 在類別、 結構、 模組或介面層級，任何程序之外宣告列舉類型是*成員列舉*。 它是類別、 結構、 模組或介面宣告它的成員。  
  
 成員列舉型別可以從任何地方內存取其類別、 結構、 模組或介面。 程式碼外部類別、 結構或模組必須限定成員列舉型別的名稱，該類別、 結構或模組的名稱。 您可以避免需要使用完整限定的名稱，藉由新增[匯入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)原始程式檔陳述式。  
  
 在命名空間層級，任何類別、 結構、 模組或介面外部宣告的列舉是在其出現的命名空間的成員。  
  
 *宣告內容*列舉型別必須是原始程式檔、 命名空間、 類別、 結構、 模組或介面，並且不能在程序。 如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 您可以將屬性套用至整個列舉，但不是屬於其成員個別。 屬性會提供組件的中繼資料資訊。  
  
## <a name="data-type"></a>資料類型  
 `Enum`陳述式可以宣告列舉的資料類型。 每個成員會在列舉資料類型。 您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。  
  
 如果您未指定`datatype`對於列舉型別，每個成員進行的資料型別其`initializer`。 如果您同時指定`datatype`和`initializer`的資料類型`initializer`必須可轉換為`datatype`。 如果沒有`datatype`也`initializer`沒有、 資料類型會預設為`Integer`。  
  
## <a name="initializing-members"></a>初始化成員  
 `Enum`陳述式可以初始化內容中選取成員的`memberlist`。 您使用`initializer`提供運算式，以指派的成員。  
  
 如果您未指定`initializer`成員，Visual Basic 將它初始化成零 (如果它是第一個`member`中`memberlist`)，或大於 1 以外的前置值`member`。  
  
 在每個提供的運算式`initializer`可以是常值、 已定義，其他常數和列舉成員已定義，包括先前的成員，這個列舉型別之任何組合。 您可以使用算術和邏輯運算子來結合這類項目。  
  
 您無法使用變數或函式中的`initializer`。 不過，您可以使用轉換關鍵字例如`CByte`和`CShort`。 您也可以使用`AscW`如果您呼叫與常數`String`或`Char`引數，因為，可以在編譯時期評估。  
  
 列舉型別不能有浮點值。 如果將浮點值指派給成員和`Option Strict`設為 on，就會發生編譯器錯誤。 如果`Option Strict`已關閉，值會自動轉換為`Enum`型別。  
  
 如果成員的值超過允許的範圍為基礎的資料類型，或如果您初始化基礎資料類型所允許的最大值的任何成員，編譯器會回報錯誤。  
  
## <a name="modifiers"></a>修飾詞  
 類別、 結構、 模組和介面的成員列舉型別預設為公用存取。 您可以調整其存取層級，使用存取修飾詞。 命名空間成員列舉型別預設為 friend 存取權限。 您可以調整其存取層級為公開，但不是屬於私用或受保護。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
 所有列舉型別成員具有公用存取，且您無法使用任何存取修飾詞在其上。 不過，如果列舉型別本身會有更多限制的存取層級，指定之列舉的存取層級會優先使用。  
  
 根據預設，所有列舉型別是型別，其欄位是常數。 因此`Shared`， `Static`，和`ReadOnly`宣告列舉型別或其成員時，就無法使用關鍵字。  
  
## <a name="assigning-multiple-values"></a>指派多個值  
 列舉型別通常代表互斥的值。 藉由<xref:System.FlagsAttribute>屬性`Enum`宣告中，您可以改為將指派多個值執行個體的列舉型別。 <xref:System.FlagsAttribute>屬性會指定列舉視為位元欄位，也就是一組旗標。 這種讀取稱為*位元*列舉型別。  
  
 當您使用宣告列舉<xref:System.FlagsAttribute>屬性，我們建議您使用是 2、 1、 2、 4、 8、 16 和等等的次方值。 我們也建議"None"是的成員，其值為 0 的名稱。 如需其他指導方針，請參閱<xref:System.FlagsAttribute>和<xref:System.Enum>。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`Enum`陳述式。 請注意，成員指`EggSizeEnum.Medium`，而不是`Medium`。  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例中的方法是外部`Egg`類別。 因此，`EggSizeEnum`是完整限定為`Egg.EggSizeEnum`。  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>範例  
 下列範例會使用`Enum`陳述式來定義一組相關的具名常數的值。 在此案例中的值是設計為資料庫的資料輸入表單時，可能會選擇的色彩。  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例顯示包含正數和負數的值。  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>範例  
 在下列範例中，`As`子句用來指定`datatype`的列舉型別。  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>範例  
 下列範例會示範如何使用位元列舉。 多個值可以指派給位元列舉型別的執行個體。 `Enum`宣告包含<xref:System.FlagsAttribute>屬性，表示列舉型別可以視為一組旗標。  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>範例  
 下列範例會逐一列舉型別。 它會使用<xref:System.Enum.GetNames%2A>方法來擷取列舉中的成員名稱的陣列和<xref:System.Enum.GetValues%2A>擷取成員值的陣列。  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [隱含和明確轉換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [常數和列舉](../../../visual-basic/language-reference/constants-and-enumerations.md)
