---
title: "如何：決定與列舉值關聯的字串 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e2b0cfa6b1e426b38198581c7d493c8907b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="19f6b-102">如何：決定與列舉值關聯的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19f6b-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="19f6b-103"><xref:System.Enum.GetValues%2A>和<xref:System.Enum.GetNames%2A>方法可讓您判斷字串和列舉成員相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="19f6b-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="19f6b-104">若要決定與列舉型別相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="19f6b-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="19f6b-105">使用<xref:System.Enum.GetNames%2A>方法來擷取列舉成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="19f6b-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="19f6b-106">這個範例會宣告列舉， `flavorEnum`，然後使用<xref:System.Enum.GetNames%2A>方法，以顯示每個成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="19f6b-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19f6b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19f6b-107">See Also</span></span>  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [<span data-ttu-id="19f6b-108">如何： 宣告列舉</span><span class="sxs-lookup"><span data-stu-id="19f6b-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="19f6b-109">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="19f6b-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="19f6b-110">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="19f6b-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="19f6b-111">如何： 逐一查看 Visual Basic 中列舉類型</span><span class="sxs-lookup"><span data-stu-id="19f6b-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="19f6b-112">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="19f6b-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="19f6b-113">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="19f6b-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
