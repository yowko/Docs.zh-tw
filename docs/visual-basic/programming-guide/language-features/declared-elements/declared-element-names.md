---
title: Declared Element Names
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: e8620517b934a5f1a97ea25c5a94c8b932bb47b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345423"
---
# <a name="declared-element-names-visual-basic"></a>宣告項目名稱 (Visual Basic)
Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.  
  
## <a name="rules"></a>規則  
 An element name in Visual Basic must observe the following rules:  
  
- It must begin with an alphabetic character or an underscore (`_`).  
  
- It must only contain alphabetic characters, decimal digits, and underscores.  
  
- It must contain at least one alphabetic character or decimal digit if it begins with an underscore.  
  
- It must not be more than 1023 characters long.  
  
 The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 The following example shows some valid element names.  
  
 `aB123__45`  
  
 `_567`  
  
 The following example shows some invalid element names. The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names. However, an underscore in any other position in an element name is CLS-compliant.  
  
### <a name="name-length-guidelines"></a>Name Length Guidelines  
 As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element. This improves the readability of your code and reduces line length and source-file size.  
  
 On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it. This is important for the readability of your code. If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.  
  
## <a name="escaped-names"></a>Escaped Names  
 Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`. However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`). An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity. You also use the brackets when you refer to the name later in your code.  
  
 In general, you should use escaped names only when:  
  
- Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or  
  
- You are working with code written in another language in which the given keyword is not reserved.  
  
 Otherwise, you should consider renaming the element if its name conflicts with a keyword. The integrated development environment (IDE) provides an easy way to do this. For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).  
  
## <a name="case-sensitivity-in-names"></a>Case Sensitivity in Names  
 Element names in Visual Basic are case-insensitive. This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name. 例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。  
  
 However, the common language runtime (CLR) uses case-sensitive binding. 因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。 例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。 If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element. 因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。  
  
## <a name="names-and-locales"></a>Names and Locales  
 Comparison of names is independent of locale. If two names match in one locale, they are guaranteed to match in all locales.  
  
## <a name="see-also"></a>請參閱

- [宣告項目](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [陳述式](../../../../visual-basic/language-reference/statements/index.md)
