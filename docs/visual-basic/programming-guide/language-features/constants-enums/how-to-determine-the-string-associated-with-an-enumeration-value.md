---
title: 如何：決定與列舉值關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414462"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="5632c-102">如何：決定與列舉值關聯的字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5632c-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="5632c-103"><xref:System.Enum.GetValues%2A>和 <xref:System.Enum.GetNames%2A> 方法可讓您判斷與列舉成員相關聯的字串和值。</span><span class="sxs-lookup"><span data-stu-id="5632c-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="5632c-104">若要判斷與列舉相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="5632c-104">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="5632c-105">使用 <xref:System.Enum.GetNames%2A> 方法來抓取與列舉成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="5632c-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="5632c-106">這個範例會宣告列舉， `flavorEnum` 然後使用 <xref:System.Enum.GetNames%2A> 方法來顯示與每個成員相關聯的字串。</span><span class="sxs-lookup"><span data-stu-id="5632c-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5632c-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5632c-107">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="5632c-108">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="5632c-108">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="5632c-109">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="5632c-109">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="5632c-110">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="5632c-110">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="5632c-111">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="5632c-111">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="5632c-112">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="5632c-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="5632c-113">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="5632c-113">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
