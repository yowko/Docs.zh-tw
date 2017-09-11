---
title: "何時使用列舉型別 (Visual Basic) |Microsoft 文件"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3853950382fd4336c569f9d772aea3c1312f2ebc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="ad6ff-102">何時使用列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad6ff-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="ad6ff-103">列舉型別能夠讓您輕鬆與集合相關的常數。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="ad6ff-104">列舉，或`Enum`，是一組值的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="ad6ff-105">列舉型別會被視為資料類型，您可以使用它們來建立使用常數之集合的變數和屬性。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="ad6ff-106">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="ad6ff-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="ad6ff-107">每當程序會接受一組有限的變數，請考慮使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="ad6ff-108">列舉型別可讓更清楚且更容易閱讀的程式碼，特別是當使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="ad6ff-109">使用列舉型別的優點包括︰</span><span class="sxs-lookup"><span data-stu-id="ad6ff-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="ad6ff-110">減少因調換或輸錯數字的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="ad6ff-111">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="ad6ff-112">讓程式碼更方便閱讀，這表示它是比較不可能的錯誤會蔓延到它。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="ad6ff-113">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-113">Ensures forward compatibility.</span></span> <span data-ttu-id="ad6ff-114">列舉型別，程式碼就比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="ad6ff-115">命名的列舉型別</span><span class="sxs-lookup"><span data-stu-id="ad6ff-115">Naming Enumerations</span></span>  
 <span data-ttu-id="ad6ff-116">使用列舉型別成員的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="ad6ff-117">當[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]遇到列舉成員名稱可能會擲回例外狀況，如果其他參考的型別程式庫包含相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-117">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="ad6ff-118">使用唯一的前置詞來識別您的應用程式或元件的值。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="ad6ff-119">當參考列舉型別的成員，您必須限定成員名稱的列舉型別名稱，或是使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="ad6ff-120">如需詳細資訊，請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="ad6ff-121">預先定義的列舉型別</span><span class="sxs-lookup"><span data-stu-id="ad6ff-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ad6ff-122">提供了數個預先定義的列舉型別，例如`FirstDayOfWeek`和`MsgBoxResul`t，以幫助您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResul`t, to facilitate your code.</span></span> <span data-ttu-id="ad6ff-123">針對這些項目的清單，請參閱[常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="ad6ff-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad6ff-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad6ff-124">See Also</span></span>  
 <span data-ttu-id="ad6ff-125">[如何︰ 宣告列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-125">[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="ad6ff-126"> [如何︰ 參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-126"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="ad6ff-127"> [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-127"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="ad6ff-128"> [如何︰ 逐一查看在 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-128"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="ad6ff-129"> [如何︰ 決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-129"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="ad6ff-130"> [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ad6ff-130"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="ad6ff-131"> [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="ad6ff-131"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
