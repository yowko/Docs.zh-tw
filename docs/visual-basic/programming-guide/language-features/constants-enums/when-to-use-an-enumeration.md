---
title: 何時使用列舉類型
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: 7b1b269a5d28d89cd491bac88fbefd4547fdc3c3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095625"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="02f10-102">何時使用列舉 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02f10-102">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="02f10-103">列舉提供簡單的方式來處理相關的常數集合。</span><span class="sxs-lookup"><span data-stu-id="02f10-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="02f10-104">列舉型別（enumeration） `Enum` 是一組值的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="02f10-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="02f10-105">列舉會視為資料類型，您可以使用它們來建立常數集合，以搭配變數和屬性使用。</span><span class="sxs-lookup"><span data-stu-id="02f10-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="02f10-106">何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="02f10-106">When to Use an Enumeration</span></span>  

 <span data-ttu-id="02f10-107">每當程式接受一組有限的變數時，請考慮使用列舉。</span><span class="sxs-lookup"><span data-stu-id="02f10-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="02f10-108">列舉可讓您更清楚且更容易閱讀的程式碼，特別是在使用有意義的名稱時。</span><span class="sxs-lookup"><span data-stu-id="02f10-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="02f10-109">使用列舉的優點包括：</span><span class="sxs-lookup"><span data-stu-id="02f10-109">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="02f10-110">減少轉置或不正確的數位所造成的錯誤。</span><span class="sxs-lookup"><span data-stu-id="02f10-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="02f10-111">可讓您在未來輕鬆變更值。</span><span class="sxs-lookup"><span data-stu-id="02f10-111">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="02f10-112">使程式碼更容易閱讀，這表示錯誤不太可能會蔓延到其中。</span><span class="sxs-lookup"><span data-stu-id="02f10-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="02f10-113">確保向前相容性。</span><span class="sxs-lookup"><span data-stu-id="02f10-113">Ensures forward compatibility.</span></span> <span data-ttu-id="02f10-114">使用列舉時，如果未來有人變更對應到成員名稱的值，您的程式碼比較不可能失敗。</span><span class="sxs-lookup"><span data-stu-id="02f10-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="02f10-115">命名列舉</span><span class="sxs-lookup"><span data-stu-id="02f10-115">Naming Enumerations</span></span>  

 <span data-ttu-id="02f10-116">使用列舉成員的命名慣例。</span><span class="sxs-lookup"><span data-stu-id="02f10-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="02f10-117">當 Visual Basic 遇到列舉成員名稱時，如果其他參考的類型程式庫包含相同的名稱，則可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="02f10-117">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="02f10-118">使用可識別應用程式或元件值的唯一前置詞。</span><span class="sxs-lookup"><span data-stu-id="02f10-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="02f10-119">參考列舉的成員時，您必須以列舉名稱來限定成員名稱，否則請使用 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="02f10-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="02f10-120">如需詳細資訊，請參閱列舉 [和名稱限定](enumerations-and-name-qualification.md)性。</span><span class="sxs-lookup"><span data-stu-id="02f10-120">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="02f10-121">預先定義的列舉</span><span class="sxs-lookup"><span data-stu-id="02f10-121">Predefined Enumerations</span></span>  

 <span data-ttu-id="02f10-122">Visual Basic 提供許多預先定義的列舉，例如 `FirstDayOfWeek` 和 `MsgBoxResult` ，以加速您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="02f10-122">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="02f10-123">如需這些的詳細清單 [，請參閱常數和](../../../language-reference/constants-and-enumerations.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="02f10-123">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f10-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f10-124">See also</span></span>

- [<span data-ttu-id="02f10-125">如何：宣告列舉類型</span><span class="sxs-lookup"><span data-stu-id="02f10-125">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="02f10-126">如何：參考列舉類型成員</span><span class="sxs-lookup"><span data-stu-id="02f10-126">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="02f10-127">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="02f10-127">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="02f10-128">如何：在 Visual Basic 中逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="02f10-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="02f10-129">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="02f10-129">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="02f10-130">End 陳述式</span><span class="sxs-lookup"><span data-stu-id="02f10-130">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="02f10-131">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="02f10-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
