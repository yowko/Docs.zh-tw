---
title: "如何：控制變數的可用性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="935eb-102">如何：控制變數的可用性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="935eb-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="935eb-103">指定控制變數的可用性其*存取層級*。</span><span class="sxs-lookup"><span data-stu-id="935eb-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="935eb-104">存取層級決定何種程式碼有權讀取或寫入的變數。</span><span class="sxs-lookup"><span data-stu-id="935eb-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="935eb-105">*成員變數*（定義在模組層級以及任何程序之外） 預設為公用存取，這表示可以看到它們的任何程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="935eb-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="935eb-106">您可以指定存取修飾詞來變更。</span><span class="sxs-lookup"><span data-stu-id="935eb-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="935eb-107">*本機變數*（定義在程序） 名義具有公用存取，雖然其程序內的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="935eb-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="935eb-108">您無法變更存取層級的區域變數，但您可以變更包含它的程序的存取層級。</span><span class="sxs-lookup"><span data-stu-id="935eb-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="935eb-109">如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="935eb-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="935eb-110">私人和公用存取</span><span class="sxs-lookup"><span data-stu-id="935eb-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="935eb-111">若要存取只會從其模組、 類別或結構中的變數</span><span class="sxs-lookup"><span data-stu-id="935eb-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="935eb-112">位置[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)變數內模組、 類別或結構，但以外的任何程序。</span><span class="sxs-lookup"><span data-stu-id="935eb-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="935eb-113">包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="935eb-114">您可以讀取或寫入變數從模組、 類別或結構中的任何位置，而不是從外部。</span><span class="sxs-lookup"><span data-stu-id="935eb-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="935eb-115">若要存取的任何程式碼，可以看到變數</span><span class="sxs-lookup"><span data-stu-id="935eb-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="935eb-116">為成員變數，請將`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="935eb-117">包含[公用](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="935eb-118">您可以讀取或寫入至變數從相互操作的任何程式碼與組件。</span><span class="sxs-lookup"><span data-stu-id="935eb-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="935eb-119">-或-</span><span class="sxs-lookup"><span data-stu-id="935eb-119">-or-</span></span>  
  
1.  <span data-ttu-id="935eb-120">為區域變數，請將`Dim`陳述式的程序內的變數。</span><span class="sxs-lookup"><span data-stu-id="935eb-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="935eb-121">不包含`Public`關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="935eb-122">您可以讀取或寫入變數，從程序中的任何位置，而不是從外部。</span><span class="sxs-lookup"><span data-stu-id="935eb-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="935eb-123">保護和 Friend 存取權限</span><span class="sxs-lookup"><span data-stu-id="935eb-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="935eb-124">您可以限制變數對其類別和任何衍生的類別，或其組件的存取層級。</span><span class="sxs-lookup"><span data-stu-id="935eb-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="935eb-125">您也可以指定這些限制，讓存取的程式碼，在任何衍生類別中或在相同的組件中的任何其他地方的聯集。</span><span class="sxs-lookup"><span data-stu-id="935eb-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="935eb-126">您指定這個聯集結合`Protected`和`Friend`相同宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="935eb-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="935eb-127">若要只能從其類別和任何衍生的類別中存取變數</span><span class="sxs-lookup"><span data-stu-id="935eb-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="935eb-128">位置`Dim`陳述式的類別內部，但任何程序之外的變數。</span><span class="sxs-lookup"><span data-stu-id="935eb-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="935eb-129">包含[保護](../../../../visual-basic/language-reference/modifiers/protected.md)關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="935eb-130">您可以讀取或寫入變數，從類別內的任何位置，以及從任何類別衍生，而不是從外部衍生鏈結中的任何類別。</span><span class="sxs-lookup"><span data-stu-id="935eb-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="935eb-131">若要在相同的組件內只能從存取變數</span><span class="sxs-lookup"><span data-stu-id="935eb-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="935eb-132">位置`Dim`變數內模組、 類別或結構，但以外的任何程序陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="935eb-133">包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="935eb-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="935eb-134">您可以讀取或寫入變數從模組、 類別或結構中的任何位置，以及從任何程式碼相同的組件，而不是從外部組件。</span><span class="sxs-lookup"><span data-stu-id="935eb-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="935eb-135">範例</span><span class="sxs-lookup"><span data-stu-id="935eb-135">Example</span></span>  
 <span data-ttu-id="935eb-136">下列範例顯示的變數宣告`Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`存取層級。</span><span class="sxs-lookup"><span data-stu-id="935eb-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="935eb-137">請注意，當`Dim`陳述式指定的存取層級，您不需要包含`Dim`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="935eb-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="935eb-138">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="935eb-138">.NET Framework Security</span></span>  
 <span data-ttu-id="935eb-139">更嚴格的變數的存取層級，小惡意程式碼的機會使用它。</span><span class="sxs-lookup"><span data-stu-id="935eb-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="935eb-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="935eb-140">See Also</span></span>  
 [<span data-ttu-id="935eb-141">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="935eb-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="935eb-142">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="935eb-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="935eb-143">Public</span><span class="sxs-lookup"><span data-stu-id="935eb-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="935eb-144">Protected</span><span class="sxs-lookup"><span data-stu-id="935eb-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="935eb-145">Friend</span><span class="sxs-lookup"><span data-stu-id="935eb-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="935eb-146">Private</span><span class="sxs-lookup"><span data-stu-id="935eb-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
