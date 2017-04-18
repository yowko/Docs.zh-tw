---
title: "Mid 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.MidB
- vb.Mid
dev_langs:
- VB
helpviewer_keywords:
- substrings, Mid statement
- strings [Visual Basic], substrings
- Mid statement
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e385d6838daa16d45903c6b270fc47ad88797845
ms.lasthandoff: 03/13/2017

---
# <a name="mid-statement"></a>Mid 陳述式
取代指定的字元數`String`變數與另一個字串的字元。  
  
## <a name="syntax"></a>語法  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>組件  
 `Target`  
 必要項。 名稱`String`若要修改的變數。  
  
 `Start`  
 必要項。 `Integer`運算式。 字元位置`Target`取代文字的開始位置。 `Start`使用起始的索引。  
  
 `Length`  
 選擇項。 `Integer`運算式。 要取代的字元數。 如果省略，所有的`String`用。  
  
 `StringExpression`  
 必要項。 `String`取代部份的運算式`Target`。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException></xref:System.ArgumentException>|`Start`<= 0="" or=""></=>`Length`< 0.></ 0.>|  
  
## <a name="remarks"></a>備註  
 被取代的字元數目一律為小於或等於中的字元數`Target`。  
  
 Visual Basic 也有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函式和`Mid`陳述式。</xref:Microsoft.VisualBasic.Strings.Mid%2A> 這些項目都會運作指定的字串中的字元數，但`Mid`函式傳回的字元時`Mid`陳述式會取代字元。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。</xref:Microsoft.VisualBasic.Strings.Mid%2A>  
  
> [!NOTE]
>  `MidB`舊版的 Visual Basic 的陳述式可以取代位元組，而不是字元的子字串。 它是主要用於轉換雙位元組字元集 (DBCS) 應用程式中的字串。 所有的 Visual Basic 字串是在 Unicode 中，和`MidB`不受支援。  
  
## <a name="example"></a>範例  
 這個範例會使用`Mid`陳述式來取代指定的字串變數中的字元數，另一個字串的字元。  
  
 [!code-vb[VbVbalrStrings #&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>需求  
 **命名空間︰** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module:**`Strings`  
  
 **組件︰**[!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [字串](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [在 Visual Basic 中的字串簡介](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
