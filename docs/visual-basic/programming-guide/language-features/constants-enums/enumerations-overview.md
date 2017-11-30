---
title: "列舉類型的概觀 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, enumerations
- enumerations [Visual Basic], about enumerations
ms.assetid: b42a38ee-5e77-4f99-a037-e3a127ead89c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d50e6bae880e5dc4dcde203708c6b07c05bb4e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-overview-visual-basic"></a><span data-ttu-id="7f5f9-102">列舉類型的概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f5f9-102">Enumerations Overview (Visual Basic)</span></span>
<span data-ttu-id="7f5f9-103">列舉型別提供便利的方式來處理組相關的常數和常數值與名稱。</span><span class="sxs-lookup"><span data-stu-id="7f5f9-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="7f5f9-104">例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。</span><span class="sxs-lookup"><span data-stu-id="7f5f9-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
## <a name="tasks-involving-enumerations"></a><span data-ttu-id="7f5f9-105">包含列舉工作</span><span class="sxs-lookup"><span data-stu-id="7f5f9-105">Tasks involving Enumerations</span></span>  
 <span data-ttu-id="7f5f9-106">下表列出常見的工作都涉及列舉型別。</span><span class="sxs-lookup"><span data-stu-id="7f5f9-106">The following table lists common tasks involving enumerations.</span></span>  
  
|<span data-ttu-id="7f5f9-107">若要執行此工作</span><span class="sxs-lookup"><span data-stu-id="7f5f9-107">To do this</span></span>|<span data-ttu-id="7f5f9-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5f9-108">See</span></span>|  
|----------------|---------|  
|<span data-ttu-id="7f5f9-109">找不到預先定義的列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-109">Find a pre-defined enumeration</span></span>|[<span data-ttu-id="7f5f9-110">常數和列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-110">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|  
|<span data-ttu-id="7f5f9-111">宣告列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-111">Declare an enumeration</span></span>|[<span data-ttu-id="7f5f9-112">如何： 宣告列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-112">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)|  
|<span data-ttu-id="7f5f9-113">完整限定名稱的列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-113">Fully qualify an enumeration's name</span></span>|[<span data-ttu-id="7f5f9-114">列舉和名稱限定性條件</span><span class="sxs-lookup"><span data-stu-id="7f5f9-114">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)|  
|<span data-ttu-id="7f5f9-115">為列舉成員，請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5f9-115">Refer to an enumeration member</span></span>|[<span data-ttu-id="7f5f9-116">如何：參考列舉成員</span><span class="sxs-lookup"><span data-stu-id="7f5f9-116">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)|  
|<span data-ttu-id="7f5f9-117">逐一查看列舉類型</span><span class="sxs-lookup"><span data-stu-id="7f5f9-117">Iterate through an enumeration</span></span>|[<span data-ttu-id="7f5f9-118">如何： 逐一查看 Visual Basic 中列舉類型</span><span class="sxs-lookup"><span data-stu-id="7f5f9-118">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)|  
|<span data-ttu-id="7f5f9-119">決定與列舉型別相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="7f5f9-119">Determine the string associated with an enumeration</span></span>|[<span data-ttu-id="7f5f9-120">如何：決定與列舉值相關聯的字串</span><span class="sxs-lookup"><span data-stu-id="7f5f9-120">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)|  
|<span data-ttu-id="7f5f9-121">決定何時使用列舉類型</span><span class="sxs-lookup"><span data-stu-id="7f5f9-121">Decide when to use an enumeration</span></span>|[<span data-ttu-id="7f5f9-122">何時使用列舉</span><span class="sxs-lookup"><span data-stu-id="7f5f9-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)|  
  
## <a name="see-also"></a><span data-ttu-id="7f5f9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5f9-123">See Also</span></span>  
 [<span data-ttu-id="7f5f9-124">常數的概觀</span><span class="sxs-lookup"><span data-stu-id="7f5f9-124">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="7f5f9-125">使用者定義的常數</span><span class="sxs-lookup"><span data-stu-id="7f5f9-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [<span data-ttu-id="7f5f9-126">如何：宣告常數</span><span class="sxs-lookup"><span data-stu-id="7f5f9-126">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [<span data-ttu-id="7f5f9-127">常數和常值資料類型</span><span class="sxs-lookup"><span data-stu-id="7f5f9-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="7f5f9-128">Enum 陳述式</span><span class="sxs-lookup"><span data-stu-id="7f5f9-128">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)
