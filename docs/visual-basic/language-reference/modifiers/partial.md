---
title: "Partial (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Partial"
  - "partial"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structures, partial"
  - "classes [Visual Basic]"
  - "partial, types [Visual Basic]"
  - "partial, structures"
  - "partial, classes [Visual Basic]"
  - "classes [Visual Basic], partial"
  - "Partial keyword [Visual Basic]"
  - "type promotion"
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: 36
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 36
---
# Partial (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示類別宣告為類型的部分定義。  
  
 您可以使用 `Partial` 關鍵字，將一個類型的定義分割成數個宣告。  您可以在任意數目的不同原始程式檔中，使用任意數目的部分宣告。  不過，所有宣告都必須位於相同的組件和相同的命名空間中。  
  
> [!NOTE]
>  Visual Basic 支援「*部分方法*」，這通常是在部分類別中實作。  如需詳細資訊，請參閱[Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)和 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
## 語法  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`attrlist`|選擇項。  套用至此類型的屬性清單。  您必須將[Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)放在角括號中 \(`< >`\)。|  
|`accessmodifier`|選擇項。  指定哪些程式碼可以存取此類型。  請參閱 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。|  
|`Shadows`|選擇項。  請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。|  
|`MustInherit`|選擇項。  請參閱 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。|  
|`NotInheritable`|選擇項。  請參閱 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)。|  
|`name`|必要項。  此類型的名稱。  必須符合相同類型的所有其他部分宣告中定義的名稱。|  
|`Of`|選擇項。  指定這是否為泛型類型。  請參閱 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)。|  
|`typelist`|如果您使用 [Of](../../../visual-basic/language-reference/statements/of-clause.md)，則此為必要項。  請參閱[Type List](../../../visual-basic/language-reference/statements/type-list.md)。|  
|`Inherits`|選擇項。  請參閱 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)。|  
|`classname`|如果您使用 `Inherits`，則此為必要項。  此類別衍生自的類別或介面名稱。|  
|`Implements`|選擇項。  請參閱 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)。|  
|`interfacenames`|如果您使用 `Implements`，則此為必要項。  此類型實作的介面名稱。|  
|`variabledeclarations`|選擇項。  宣告類型的其他變數和事件的陳述式。|  
|`proceduredeclarations`|選擇項。  宣告和定義類型的其他程序的陳述式。|  
|`End Class` 或 `End Structure`|結束此部分 `Class` 或 `Structure` 定義。|  
  
## 備註  
 Visual Basic 使用部分類別定義來劃分個別原始程式檔中產生的程式碼與使用者撰寫的程式碼。  例如，\[**Windows Form 設計工具**\] 定義控制項的部分類別，例如 <xref:System.Windows.Forms.Form>。  您不應該在這些控制項中修改產生的程式碼。  
  
 建立部分類型時會套用類別、結構、介面和模組建立的所有規則，例如修飾詞的使用方式和繼承。  
  
## 最佳作法  
  
-   在正常情況下，您不該將單一類型的開發分成兩個或多個宣告。  因此，在大部分情況下您不需要 `Partial` 關鍵字。  
  
-   為了便於閱讀，類型的每個部分宣告都應該包含 `Partial` 關鍵字。  編譯器最多允許一個部分宣告省略關鍵字；如果有兩個或多個部分宣告省略關鍵字，則編譯器會發出錯誤訊號。  
  
## 行為  
  
-   **宣告的等位。** 編譯器會將此類型視為其所有部分宣告的等位。  每個部分定義的每個修飾詞都會套用至整個類型，而每個部分定義的每個成員均可用於整個類型。  
  
-   **模組中的部分類型不允許類型提升。** 如果部分定義在某個模組內，則該類型的類型提升會自動失效。  在這種情況下，一組部分定義可能會導致非預期的結果，甚至是編譯器錯誤。  如需詳細資訊，請參閱[Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)。  
  
     只有在完整路徑相同時，編譯器才會合併部分定義。  
  
 `Partial` 關鍵字可用於以下內容：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## 範例  
 下列範例會將 `sampleClass` 類別的定義分割成兩個宣告，每個定義可定義不同的 `Sub` 程序。  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/visualbasic/partial_1.vb)]  
  
 上述範例中的兩個部分定義可位於相同的原始程式檔或在兩個不同的原始程式檔中。  
  
## 請參閱  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Type Promotion](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)   
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Visual Basic 中的泛型類型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)