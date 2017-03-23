---
title: "Differences Between Shadowing and Overriding (Visual Basic) | Microsoft Docs"
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
  - "shadowing, vs. overriding"
  - "overriding, vs. shadowing"
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Differences Between Shadowing and Overriding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當您定義繼承自基底類別的類別，有時需要在衍生類別 \(Derived Class\) 中重新定義一個或多個基底類別，  此時可以使用遮蔽和覆寫。  
  
## 比較  
 遮蔽和覆寫都是用於繼承自基底類別的衍生類別，也都會以宣告項目重新定義另一個宣告項目。  但是其間還是有許多不同之處。  
  
 下表對遮蔽和覆寫進行比較。  
  
||||  
|-|-|-|  
|比較要點|遮蔽|覆寫|  
|用途|避免後續基底類別修改，這種修改會引入已在衍生類別中定義的成員|以相同呼叫順序<sup>1</sup> 定義不同的程序或屬性實作，以達到多型 \(Polymorphism\)|  
|重新定義的項目|何宣告項目型別|只有程序 \(`Function`、`Sub` 或 `Operator`\) 或屬性|  
|重新定義項目|何宣告項目型別|只有具有相同呼叫順序的程序或屬性<sup>1</sup>|  
|重新定義項目的存取層級|任何存取層級|無法變更覆寫項目的存取層級|  
|重新定義項目的可讀性與可寫性|任何組合|無法變更覆寫屬性的可讀性或可寫性|  
|重新定義的控制|基底類別 \(Base Class\) 項目無法強制或禁止遮蔽|基底類別 \(Base Class\) 項目可以指定 `MustOverride`、`NotOverridable` 或 `Overridable`|  
|關鍵字用法|在衍生類別中建議使用 `Shadows`，如果沒有指定 `Shadows` 或 `Overrides`，則使用 `Shadows`<sup>2</sup>|在基底類別中必須使用 `Overridable` 或 `MustOverride`，在衍生類別中必須使用 `Overrides`|  
|以衍生自您所衍生類別的類別繼承重新定義項目|主導遮蔽項目 \(Shadowing Element\) 是以衍生自衍生類別的類別來繼承，受遮蔽項目 \(Shadowed Element\) 還是隱藏的<sup>3</sup>|覆寫項目是以其他的衍生類別來繼承；被覆寫的項目還是覆寫的|  
  
 <sup>1</sup>「*呼叫順序*」\(Calling Sequence\) 是由項目型別 \(`Function`、`Sub`、`Operator` 或 `Property`\)、名稱、參數清單和傳回型別所組成。  您無法以屬性覆寫程序，也無法以程序覆寫屬性。  您無法以另一種程序覆寫某種程序 \(`Function`、`Sub` 或 `Operator`\)。  
  
 <sup>2</sup> 如果您沒有指定 `Shadows` 或 `Overrides`，編譯器會發出警告訊息，幫助您確認要使用哪一種重複定義。  如果您忽略警告，則會使用遮蔽機制。  
  
 <sup>3</sup> 如果主導遮蔽項目 \(Shadowing Element\) 無法在衍生自衍生類別的類別中存取，表示未繼承遮蔽。  例如，如果您將主導遮蔽項目 \(Shadowing Element\) 宣告為 `Private`，衍生自衍生類別的類別會繼承原來的項目，而非主導遮蔽項目 \(Shadowing Element\)。  
  
## 方針  
 一般會在下列情況下使用遮蔽：  
  
-   正在定義多型衍生類別 \(Derived Class\)。  
  
-   要讓編譯器強制項目型別與呼叫順序一致以維護安全。  
  
 一般會在下列情況下使用覆寫：  
  
-   預期基底類別 \(Base Class\) 已經修改過，並使用相同名稱定義項目。  
  
-   要自由變更項目型別或呼叫順序。  
  
## 請參閱  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)