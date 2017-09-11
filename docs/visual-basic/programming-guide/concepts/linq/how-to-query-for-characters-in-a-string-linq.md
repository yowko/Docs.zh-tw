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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dabd63e52707f3078c6cdc41db8c4f0e7dfbf70e
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-characters-in-a-string-linq-visual-basic"></a><span data-ttu-id="9922f-102">如何︰ 查詢字串 (LINQ) (Visual Basic) 中的字元</span><span class="sxs-lookup"><span data-stu-id="9922f-102">How to: Query for Characters in a String (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="9922f-103">因為<xref:System.String>類別會實作泛型<xref:System.Collections.Generic.IEnumerable%601>介面，可以查詢的任何字串，形式為一連串字元。</xref:System.Collections.Generic.IEnumerable%601> </xref:System.String></span><span class="sxs-lookup"><span data-stu-id="9922f-103">Because the <xref:System.String> class implements the generic <xref:System.Collections.Generic.IEnumerable%601> interface, any string can be queried as a sequence of characters.</span></span> <span data-ttu-id="9922f-104">不過，這不是 LINQ 的一般用途。</span><span class="sxs-lookup"><span data-stu-id="9922f-104">However, this is not a common use of LINQ.</span></span> <span data-ttu-id="9922f-105">對於複雜的模式比對作業，使用<xref:System.Text.RegularExpressions.Regex>類別。</xref:System.Text.RegularExpressions.Regex></span><span class="sxs-lookup"><span data-stu-id="9922f-105">For complex pattern matching operations, use the <xref:System.Text.RegularExpressions.Regex> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9922f-106">範例</span><span class="sxs-lookup"><span data-stu-id="9922f-106">Example</span></span>  
 <span data-ttu-id="9922f-107">下列範例會查詢以判斷它所包含的數字的數字的字串。</span><span class="sxs-lookup"><span data-stu-id="9922f-107">The following example queries a string to determine the number of numeric digits it contains.</span></span> <span data-ttu-id="9922f-108">請注意，查詢 「 重複使用 「 執行第一次之後。</span><span class="sxs-lookup"><span data-stu-id="9922f-108">Note that the query is "reused" after it is executed the first time.</span></span> <span data-ttu-id="9922f-109">這可能是因為查詢本身不會儲存任何實際的結果。</span><span class="sxs-lookup"><span data-stu-id="9922f-109">This is possible because the query itself does not store any actual results.</span></span>  
  
<span data-ttu-id="9922f-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="9922f-110"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="compiling-the-code"></a><span data-ttu-id="9922f-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9922f-111">Compiling the Code</span></span>  
 <span data-ttu-id="9922f-112">建立以.NET Framework 3.5 版或以上版本，搭配 system.core.dll 的參考目標的專案和`Imports`System.Linq 命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="9922f-112">Create a project that targets the .NET Framework version 3.5 or higher with a reference to System.Core.dll and a `Imports` statement for the System.Linq namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9922f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9922f-113">See Also</span></span>  
 <span data-ttu-id="9922f-114">[LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="9922f-114">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="9922f-115"> [如何︰ 合併 LINQ 查詢與規則運算式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="9922f-115"> [How to: Combine LINQ Queries with Regular Expressions (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)</span></span>
