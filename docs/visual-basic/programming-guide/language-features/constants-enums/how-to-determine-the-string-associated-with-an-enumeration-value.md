---
title: HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 4fa04fa621347ae961975bfb636734e6c9df39fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906798"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="ade8e-102">HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="ade8e-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="ade8e-103"><xref:System.Enum.GetValues%2A>和<xref:System.Enum.GetNames%2A>方法可讓您決定的字串和列舉成員相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="ade8e-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="ade8e-104">若要決定與列舉型別相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="ade8e-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="ade8e-105">使用<xref:System.Enum.GetNames%2A>方法來擷取與列舉成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="ade8e-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="ade8e-106">這個範例會宣告列舉`flavorEnum`，然後使用<xref:System.Enum.GetNames%2A>方法，以顯示每個成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="ade8e-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ade8e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade8e-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="ade8e-108">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="ade8e-108">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="ade8e-109">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="ade8e-109">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="ade8e-110">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="ade8e-110">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="ade8e-111">如何：逐一查看 Visual Basic 中列舉</span><span class="sxs-lookup"><span data-stu-id="ade8e-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="ade8e-112">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="ade8e-112">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="ade8e-113">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="ade8e-113">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
