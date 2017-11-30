---
title: "如何：在 Visual Basic 中逐一查看列舉類型"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 439e6eae7d475316625a2cc1d3a70a9e7181f68a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="695c8-102">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="695c8-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="695c8-103">列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。</span><span class="sxs-lookup"><span data-stu-id="695c8-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="695c8-104">要逐一查看列舉類型，您可以將它移至陣列使用<xref:System.Enum.GetValues%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="695c8-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="695c8-105">您也可以逐一列舉型別使用`For...Each`陳述式中，使用<xref:System.Enum.GetNames%2A>或<xref:System.Enum.GetValues%2A>方法，可擷取的字串或數值的值。</span><span class="sxs-lookup"><span data-stu-id="695c8-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="695c8-106">若要逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="695c8-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="695c8-107">宣告陣列，並使用轉換成列舉<xref:System.Enum.GetValues%2A>方法，然後再將陣列傳遞為您將任何其他變數。</span><span class="sxs-lookup"><span data-stu-id="695c8-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="695c8-108">下列範例會顯示每個成員的列舉型別<xref:Microsoft.VisualBasic.FirstDayOfWeek>逐一查看的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="695c8-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="695c8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="695c8-109">See Also</span></span>  
 [<span data-ttu-id="695c8-110">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="695c8-110">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="695c8-111">如何： 宣告列舉</span><span class="sxs-lookup"><span data-stu-id="695c8-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="695c8-112">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="695c8-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="695c8-113">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="695c8-113">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="695c8-114">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="695c8-114">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="695c8-115">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="695c8-115">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="695c8-116">陣列</span><span class="sxs-lookup"><span data-stu-id="695c8-116">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
