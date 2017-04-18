---
title: "字串和其他類型 (Visual Basic) 之間的轉換 |Microsoft 文件"
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
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
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
ms.openlocfilehash: 2d0a5fc7327ecd6339b5021e1b4cb87cc54bd2bc
ms.lasthandoff: 03/13/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>字串與其他類型之間的轉換 (Visual Basic)
您可以將轉換的數字、 `Boolean`，或日期/時間值`String`。 您也可以反向轉換，從字串值為數值， `Boolean`，或`Date`— 提供字串的內容可以解譯為目的地資料類型的有效值。 如果它們不會發生執行階段錯誤。  
  
 所有這些指派任一方向的轉換會縮小轉換。 You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A>和<xref:Microsoft.VisualBasic.Conversion.Val%2A>函式可讓您進一步控制字串和數字之間的轉換。</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A>  
  
 如果您已經定義的類別或結構，您可以定義型別之間的轉換運算子`String`和類別或結構的類型。 如需詳細資訊，請參閱[How to︰ 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="conversion-of-numbers-to-strings"></a>數字轉換為字串  
 您可以使用`Format`函式，將數字轉換為格式化字串，其中可以包括不僅適當的數字，但也格式符號，例如貨幣符號 (例如`$`)，千位分隔符號或*數字群組符號*(例如`,`)，以及小數分隔符號 (例如`.`)。 `Format`會自動使用適當的符號，根據**地區選項**Windows 控制台中**控制台**。  
  
 請注意，串連 (`&`) 運算子可以將數字轉換成字串以隱含方式，如下列範例所示。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>字串轉換成數字  
 您可以使用`Val`函式來明確地將字串中的數字轉換為數值。 `Val`讀取字串，直到遇到數字、 空格、 索引標籤、 換行字元或句號以外的字元。 序列 「 i O 」 和 「 i H"改變基底的數字系統，並終止掃描。 在停止讀取，`Val`將所有適當的字元轉換為數值。 例如，下列陳述式會傳回值`141.825`。  
  
 `Val("   14   1.825 miles")`  
  
 當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]將轉換的數字值的字串，它會使用**地區選項**Windows 控制台中**控制台**來解譯千分位分隔符號，十進位分隔符號和貨幣符號。 這表示，轉換可能成功但不是其他設定一個。 例如，`"$14.20"`是可接受的英文 （美國） 地區設定，但不是在法文地區設定。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [如何︰ 將物件轉換成 Visual Basic 中的另一個型別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [以 .NET Framework 為基礎的國際應用程式簡介](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
