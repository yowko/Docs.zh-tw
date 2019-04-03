---
title: 何時使用列舉 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825093"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="113f2-102">何時使用列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="113f2-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="113f2-103">列舉型別能夠讓您輕鬆使用相關常數組。</span><span class="sxs-lookup"><span data-stu-id="113f2-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="113f2-104">列舉，或`Enum`，是一組值的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="113f2-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="113f2-105">列舉型別會被視為資料類型，您可以使用它們來建立變數和屬性集之常數的使用。</span><span class="sxs-lookup"><span data-stu-id="113f2-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="113f2-106">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="113f2-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="113f2-107">每當程序會接受一組有限的變數，請考慮使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="113f2-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="113f2-108">列舉型別進行更清楚且更容易閱讀的程式碼，尤其是使用有意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="113f2-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="113f2-109">使用列舉型別的優點包括：</span><span class="sxs-lookup"><span data-stu-id="113f2-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="113f2-110">減少調換，或輸入數字的錯誤所造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="113f2-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="113f2-111">可讓您輕鬆地在未來變更的值。</span><span class="sxs-lookup"><span data-stu-id="113f2-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="113f2-112">讓程式碼更方便閱讀，這表示它不太可能的錯誤會蔓延到其中。</span><span class="sxs-lookup"><span data-stu-id="113f2-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="113f2-113">可確保往後相容性。</span><span class="sxs-lookup"><span data-stu-id="113f2-113">Ensures forward compatibility.</span></span> <span data-ttu-id="113f2-114">列舉型別，與您的程式碼是比較不可能失敗，如果有人在未來變更為成員名稱的對應值。</span><span class="sxs-lookup"><span data-stu-id="113f2-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="113f2-115">命名的列舉型別</span><span class="sxs-lookup"><span data-stu-id="113f2-115">Naming Enumerations</span></span>  
 <span data-ttu-id="113f2-116">列舉成員，請使用命名慣例。</span><span class="sxs-lookup"><span data-stu-id="113f2-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="113f2-117">當 Visual Basic 會遇到的列舉型別成員名稱時，如果其他參考的型別程式庫包含相同的名稱可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="113f2-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="113f2-118">使用唯一的前置詞來識別您的應用程式或元件的值。</span><span class="sxs-lookup"><span data-stu-id="113f2-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="113f2-119">當參考的列舉型別成員，您必須限定成員名稱與列舉型別名稱，或是使用`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="113f2-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="113f2-120">如需詳細資訊，請參閱 <<c0> [ 列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。</span><span class="sxs-lookup"><span data-stu-id="113f2-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="113f2-121">預先定義的列舉型別</span><span class="sxs-lookup"><span data-stu-id="113f2-121">Predefined Enumerations</span></span>  
 <span data-ttu-id="113f2-122">Visual Basic 中提供數個預先定義的列舉型別，例如`FirstDayOfWeek`和`MsgBoxResult`，以協助您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="113f2-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="113f2-123">如需相關清單請參閱 <<c0> [ 常數和列舉型別](../../../../visual-basic/language-reference/constants-and-enumerations.md)。</span><span class="sxs-lookup"><span data-stu-id="113f2-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="113f2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="113f2-124">See also</span></span>

- [<span data-ttu-id="113f2-125">如何：宣告列舉</span><span class="sxs-lookup"><span data-stu-id="113f2-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="113f2-126">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="113f2-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="113f2-127">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="113f2-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="113f2-128">如何：逐一查看 Visual Basic 中列舉</span><span class="sxs-lookup"><span data-stu-id="113f2-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="113f2-129">如何：決定與列舉值關聯的字串</span><span class="sxs-lookup"><span data-stu-id="113f2-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="113f2-130">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="113f2-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="113f2-131">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="113f2-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
