---
title: 如何：逐一查看列舉
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: fb6fbdd45ca0e84ccb9fc55296d78e3867d5fe25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414423"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="2cae0-102">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="2cae0-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="2cae0-103">列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。</span><span class="sxs-lookup"><span data-stu-id="2cae0-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="2cae0-104">若要逐一查看列舉，您可以使用方法將它移入陣列 <xref:System.Enum.GetValues%2A> 。</span><span class="sxs-lookup"><span data-stu-id="2cae0-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="2cae0-105">您也可以使用語句逐一查看列舉 `For...Each` ，使用 <xref:System.Enum.GetNames%2A> 或 <xref:System.Enum.GetValues%2A> 方法來解壓縮字串或數值。</span><span class="sxs-lookup"><span data-stu-id="2cae0-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="2cae0-106">逐一查看列舉</span><span class="sxs-lookup"><span data-stu-id="2cae0-106">To iterate through an enumeration</span></span>  
  
- <span data-ttu-id="2cae0-107">宣告陣列，並使用方法將列舉轉換成它，然後 <xref:System.Enum.GetValues%2A> 再傳遞陣列，就像任何其他變數一樣。</span><span class="sxs-lookup"><span data-stu-id="2cae0-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="2cae0-108">下列範例 <xref:Microsoft.VisualBasic.FirstDayOfWeek> 會在逐一查看列舉時顯示列舉的每個成員。</span><span class="sxs-lookup"><span data-stu-id="2cae0-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="2cae0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cae0-109">See also</span></span>

- [<span data-ttu-id="2cae0-110">列舉的概觀</span><span class="sxs-lookup"><span data-stu-id="2cae0-110">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="2cae0-111">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="2cae0-111">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="2cae0-112">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="2cae0-112">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="2cae0-113">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="2cae0-113">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="2cae0-114">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="2cae0-114">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="2cae0-115">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="2cae0-115">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="2cae0-116">陣列</span><span class="sxs-lookup"><span data-stu-id="2cae0-116">Arrays</span></span>](../arrays/index.md)
