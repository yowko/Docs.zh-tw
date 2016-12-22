---
title: "Property Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.PropertySet"
  - "vb.Property"
  - "vb.PropertyGet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Property 陳述式"
  - "預設修飾詞"
  - "property 程序，屬性陳述式"
  - "Property 關鍵字"
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
caps.handback.revision: 41
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣告屬性的名稱，以及用以儲存及擷取屬性值的屬性程序。  
  
## <a name="syntax"></a>語法  
  
```  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
  
```  
  
## <a name="parts"></a>組件  
  
-   `attributelist`  
  
     選擇項。 適用於此屬性的屬性清單或 `Get` 或 `Set` 程序。 請參閱 [屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。  
  
-   `Default`  
  
     選擇項。 指定這個屬性是類別或結構定義所在的預設屬性。 預設屬性不能接受參數，並可以設定和擷取而不指定屬性名稱。 如果您宣告屬性做為 `Default`, ，您不能使用 `Private` 屬性或其中一個屬性程序。  
  
-   `accessmodifier`  
  
     選擇性在 `Property` 陳述式和上一個 `Get` 和 `Set` 陳述式。 可以是下列其中一項：  
  
    -   [公用](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [受保護](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [私用](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
-   `propertymodifiers`  
  
     選擇項。 可以是下列其中一項：  
  
    -   [多載](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [可覆寫](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     選擇項。 請參閱 [共用](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
-   `Shadows`  
  
     選擇項。 請參閱 [陰影](../../../visual-basic/language-reference/modifiers/shadows.md)。  
  
-   `ReadOnly`  
  
     選擇項。 請參閱 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
-   `WriteOnly`  
  
     選擇項。 請參閱 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)。  
  
-   `Iterator`  
  
     選擇項。 請參閱 [迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)。  
  
-   `name`  
  
     必要項。 屬性的名稱。 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
-   `parameterlist`  
  
     選擇項。 表示這個屬性的參數和可能的額外參數的變數名稱清單 `Set` 程序。 請參閱 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。  
  
-   `returntype`  
  
     只有在 `Option``Strict` 是 `On`。 這個屬性所傳回之值的資料型別。  
  
-   `Implements`  
  
     選擇項。 表示這個屬性會實作一個或多個屬性，每一個定義中包含這個屬性的類別或結構所實作的介面。 請參閱 [實作陳述式](../../../visual-basic/language-reference/statements/implements-statement.md)。  
  
-   `implementslist`  
  
     如果使用 `Implements`，則為必要項。 要實作的屬性清單。  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     每個 `implementedproperty` 都具有下列語法和組件：  
  
     `interface.definedname`  
  
    |||  
    |-|-|  
    |組件|說明|  
    |`interface`|必要項。 這個屬性所實作的介面名稱的包含類別或結構。|  
    |`definedname`|必要項。 此屬性定義中的名稱 `interface`。|  
  
-   `Get`  
  
     選擇項。 必要屬性標示為 `WriteOnly`。 啟動 `Get` 屬性用來傳回屬性值的程序。  
  
-   `statements`  
  
     選擇項。 在執行陳述式區塊 `Get` 或 `Set` 程序。  
  
-   `End Get`  
  
     終止 `Get` 屬性程序。  
  
-   `Set`  
  
     選擇項。 必要屬性標示為 `ReadOnly`。 啟動 `Set` 屬性用來儲存屬性值的程序。  
  
-   `End Set`  
  
     終止 `Set` 屬性程序。  
  
-   `End Property`  
  
     結束這個屬性的定義。  
  
## <a name="remarks"></a>備註  
  `Property` 陳述式會採用屬性宣告。 屬性可以有 `Get` 程序 （唯讀）， `Set` 程序 （唯寫） 或這兩個 （讀 / 寫）。 您可以省略 `Get` 和 `Set` 程序時使用自動實作的屬性。 如需詳細資訊，請參閱 [Auto-Implemented 屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。  
  
 您可以使用 `Property` 只能在類別層級。 這表示 *宣告內容* 屬性必須是類別、 結構、 模組或介面，而且不能是原始程式檔、 命名空間、 程序或區塊。 如需詳細資訊，請參閱 [宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
 根據預設，屬性會使用公用存取。 您可以調整屬性的存取層級的存取修飾詞在 `Property` 陳述式，而且您可以選擇是否要調整其中一個屬性程序更嚴格的存取層級。  
  
 Visual Basic 會將傳遞的參數 `Set` 期間屬性指派的程序。 如果您未提供的參數 `Set`, ，整合式的開發環境 (IDE) 會使用名為的隱含參數 `value`。 這個參數會保存要指派給屬性的值。 通常這個值儲存在私用的本機變數，並將它傳回每當 `Get` 呼叫程序。  
  
## <a name="rules"></a>規則  
  
-   **混合的存取層級。** 如果您正在定義的讀寫屬性，您可以選擇其中一個指定不同的存取層級 `Get` 或 `Set` 程序，但非兩者。 如果您這麼做時，程序的存取層級必須是屬性的存取層級更具限制性。 例如，如果屬性宣告 `Friend`, ，您可以宣告 `Set` 程序 `Private`, ，但不是 `Public`。  
  
     如果您要定義 `ReadOnly` 或 `WriteOnly` 屬性中的單一屬性程序 (`Get` 或 `Set`, 分別) 代表所有的屬性。 因為，則會設定屬性的兩個存取層級，您無法宣告此類的程序，不同的存取層級。  
  
-   **傳回型別。**  `Property` 陳述式可以宣告其傳回值的資料型別。 您可以指定任何資料型別或列舉、 結構、 類別或介面的名稱。  
  
     如果您未指定 `returntype`, ，該屬性傳回 `Object`。  
  
-   **實作。** 如果這個屬性會使用 `Implements` 關鍵字、 包含類別或結構必須 `Implements` 陳述式之後立即其 `Class` 或 `Structure` 陳述式。  `Implements` 陳述式必須包含在指定的每個介面 `implementslist`。 不過，名稱的介面會定義 `Property` (在 `definedname`) 並沒有這個屬性的名稱相同 (在 `name`)。  
  
## <a name="behavior"></a>行為  
  
-   **從屬性程序傳回。** 當 `Get` 或 `Set` 程序會傳回呼叫程式碼，以叫用它的陳述式之後繼續執行。  
  
      `Exit Property` 和 `Return` 陳述式而造成屬性程序立即結束。 任何數目的 `Exit Property` 和 `Return` 陳述式可以出現在任何地方程序，且您可以混合 `Exit Property` 和 `Return` 陳述式。  
  
-   **傳回值。** 若要傳回值，以從 `Get` 程序中，您可以將值指派給屬性的名稱，或將它併入 `Return` 陳述式。 下列範例將傳回值指派給屬性名稱 `quoteForTheDay` ，然後使用 `Exit Property` 陳述式來傳回。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     如果您使用 `Exit Property` 而不指派值給 `name`, 、 `Get` 程序會傳回屬性的資料類型的預設值。  
  
      `Return` 陳述式同時指派 `Get` 程序傳回值，並結束程序。 下列範例示範這點。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例會宣告類別中的屬性。  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [物件和類別](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Get 陳述式](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set 陳述式](../../../visual-basic/language-reference/statements/set-statement.md)   
 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Default](../../../visual-basic/language-reference/modifiers/default.md)