---
title: Inherits Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae9ba54c3fd1ec3332c9f6260bc19a1293270ad8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="inherits-statement"></a>Inherits Statement
會導致目前的類別或介面繼承自另一個類別或介面的集合的屬性、 變數、 屬性、 程序和事件。  
  
## <a name="syntax"></a>語法  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`basetypenames`|必要項。 這個類別衍生自類別的名稱。<br /><br /> -或-<br /><br /> 此介面衍生自介面的名稱。 使用逗號來分隔多個名稱。|  
  
## <a name="remarks"></a>備註  
 如果單獨使用，`Inherits`陳述式必須是類別或介面定義中的第一個非空白且非註解一行。 應該緊接`Class`或`Interface`陳述式。  
  
 您可以使用`Inherits`只能在類別或介面中。 這表示繼承的宣告內容不能是原始程式檔、 命名空間、 結構、 模組、 程序或區塊。  
  
## <a name="rules"></a>規則  
  
-   **類別繼承。** 如果類別使用`Inherits`陳述式中，您可以指定一個基底類別。  
  
     類別無法繼承自巢狀類別。  
  
-   **介面繼承。** 如果介面使用`Inherits`陳述式中，您可以指定一或多個基底介面。 您可以繼承自兩個介面，即使它們每個會定義具有相同名稱的成員。 如果您這樣做時，實作程式碼必須使用名稱限定性條件來指定它所實作的成員。  
  
     介面無法繼承自另一個介面具有更嚴格的存取層級。 例如，`Public`介面無法繼承自`Friend`介面。  
  
     介面無法繼承自介面巢狀。  
  
 .NET Framework 中的類別繼承的範例是<xref:System.ArgumentException>類別，繼承自<xref:System.SystemException>類別。 如此可<xref:System.ArgumentException>所有預先定義的屬性和程序所需的系統例外狀況，例如<xref:System.Exception.Message%2A>屬性和<xref:System.Exception.ToString%2A>方法。  
  
 舉例來說，.NET Framework 中的介面繼承是<xref:System.Collections.ICollection>介面，繼承自<xref:System.Collections.IEnumerable>介面。 這會導致<xref:System.Collections.ICollection>繼承需要周遊集合的列舉值的定義。  
  
## <a name="example"></a>範例  
 下列範例會使用`Inherits`陳述式來顯示類別的名稱為`thisClass`可以繼承基底類別的所有成員`anotherClass`。  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a>範例  
 下列範例顯示多個介面的繼承。  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 名為介面`thisInterface`現在包含在所有定義<xref:System.IComparable>， <xref:System.IDisposable>，和<xref:System.IFormattable>介面繼承的成員分別提供針對特定類型的比較的兩個物件，釋放配置的資源表示為物件的值和`String`。 類別可實作`thisInterface`必須實作每個基底介面的每個成員。  
  
## <a name="see-also"></a>另請參閱  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
