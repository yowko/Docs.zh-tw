---
title: "如何︰ 查詢字串 (LINQ) (Visual Basic) 中的字元 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 499ebbe0-746c-4235-9dba-ce722c12b50e
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a>如何︰ 查詢字串 (LINQ) (Visual Basic) 中的字元
因為<xref:System.String>類別會實作泛型<xref:System.Collections.Generic.IEnumerable%601>介面，可以查詢的任何字串，形式為一連串字元。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String> 不過，這不是 LINQ 的一般用途。 對於複雜的模式比對作業，使用<xref:System.Text.RegularExpressions.Regex>類別。</xref:System.Text.RegularExpressions.Regex>  
  
## <a name="example"></a>範例  
 下列範例會查詢以判斷它所包含的數字的數字的字串。 請注意，查詢 「 重複使用 「 執行第一次之後。 這可能是因為查詢本身不會儲存任何實際的結果。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## <a name="compiling-the-code"></a>編譯程式碼  
 建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [如何︰ 合併 LINQ 查詢與規則運算式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
