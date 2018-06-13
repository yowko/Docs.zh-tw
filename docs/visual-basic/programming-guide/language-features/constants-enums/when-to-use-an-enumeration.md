---
title: 何時使用列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: e50057e114abae9fbf05c94ef0b60cf94b033a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647301"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="84003-102">何時使用列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84003-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="84003-103">列舉型別能夠讓您輕鬆與集合相關的常數。</span><span class="sxs-lookup"><span data-stu-id="84003-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="84003-104">列舉，或`Enum`，是一組值的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="84003-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="84003-105">列舉型別會被視為資料類型，您可以使用它們來建立多組使用的常數與變數和屬性。</span><span class="sxs-lookup"><span data-stu-id="84003-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="84003-106">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="84003-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="84003-107">每當程序會接受一組有限的變數，請考慮使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="84003-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="84003-108">列舉型別進行更清楚且更容易閱讀的程式碼，特別是當使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="84003-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="84003-109">使用列舉的優點包括：</span><span class="sxs-lookup"><span data-stu-id="84003-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="84003-110">減少調換或輸入數字的錯誤所造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="84003-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="84003-111">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="84003-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="84003-112">讓程式碼更方便閱讀，這表示比較不可能的錯誤會漸漸它。</span><span class="sxs-lookup"><span data-stu-id="84003-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="84003-113">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="84003-113">Ensures forward compatibility.</span></span> <span data-ttu-id="84003-114">列舉型別，您的程式碼是比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="84003-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="84003-115">命名列舉型別</span><span class="sxs-lookup"><span data-stu-id="84003-115">Naming Enumerations</span></span>  
 <span data-ttu-id="84003-116">用於列舉型別成員的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="84003-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="84003-117">當 Visual Basic 遇到列舉成員名稱時，如果其他參考的型別程式庫包含相同的名稱可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="84003-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="84003-118">使用唯一的前置詞來識別您的應用程式或元件的值。</span><span class="sxs-lookup"><span data-stu-id="84003-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="84003-119">當參考的列舉成員，您必須限定成員名稱與列舉型別名稱，或是使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="84003-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="84003-120">如需詳細資訊，請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="84003-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="84003-121">預先定義的列舉型別</span><span class="sxs-lookup"><span data-stu-id="84003-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="84003-122">Visual Basic 提供了數個預先定義的列舉型別，例如`FirstDayOfWeek`和`MsgBoxResult`，以簡化您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="84003-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="84003-123">如需相關清單請參閱[常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="84003-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84003-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84003-124">See Also</span></span>  
 [<span data-ttu-id="84003-125">如何： 宣告列舉</span><span class="sxs-lookup"><span data-stu-id="84003-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="84003-126">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="84003-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="84003-127">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="84003-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="84003-128">如何： 逐一查看 Visual Basic 中列舉類型</span><span class="sxs-lookup"><span data-stu-id="84003-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="84003-129">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="84003-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="84003-130">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="84003-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="84003-131">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="84003-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
