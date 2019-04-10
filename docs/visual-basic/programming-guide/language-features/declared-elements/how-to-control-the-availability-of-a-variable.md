---
title: HOW TO：控制變數 (Visual Basic) 的可用性
ms.date: 07/20/2015
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
ms.openlocfilehash: fb400b113e3f3305f5b724734b2bf9aa9425d03f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311522"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="b7809-102">HOW TO：控制變數 (Visual Basic) 的可用性</span><span class="sxs-lookup"><span data-stu-id="b7809-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="b7809-103">指定控制變數的可用性及其*存取層級*。</span><span class="sxs-lookup"><span data-stu-id="b7809-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="b7809-104">存取層級會判斷哪些程式碼有權讀取或寫入變數。</span><span class="sxs-lookup"><span data-stu-id="b7809-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="b7809-105">*成員變數*（定義在模組層級和任何程序之外） 預設為公用存取，這表示可以看到它們的任何程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="b7809-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="b7809-106">您可以藉由指定的存取修飾詞來變更此設定。</span><span class="sxs-lookup"><span data-stu-id="b7809-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="b7809-107">*本機變數*（程序內所定義的） 名義上具有公用存取，但其程序內的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="b7809-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="b7809-108">您無法變更存取層級的區域變數，但您可以變更包含它的程序的存取層級。</span><span class="sxs-lookup"><span data-stu-id="b7809-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="b7809-109">如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="b7809-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="b7809-110">私用和公用存取</span><span class="sxs-lookup"><span data-stu-id="b7809-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="b7809-111">若要存取只能從其模組、 類別或結構中的變數</span><span class="sxs-lookup"><span data-stu-id="b7809-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="b7809-112">地方[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)內模組、 類別或結構，但在任何程序之外的變數。</span><span class="sxs-lookup"><span data-stu-id="b7809-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="b7809-113">包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="b7809-114">您可以讀取或寫入變數，從模組、 類別或結構內的任何位置，而不是從其外部。</span><span class="sxs-lookup"><span data-stu-id="b7809-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="b7809-115">若要從任何可以看到它的程式碼存取變數</span><span class="sxs-lookup"><span data-stu-id="b7809-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="b7809-116">成員變數，將`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="b7809-117">包含[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="b7809-118">您可以讀取或寫入變數的交互操作的任何程式碼與您的組件。</span><span class="sxs-lookup"><span data-stu-id="b7809-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="b7809-119">-或-</span><span class="sxs-lookup"><span data-stu-id="b7809-119">-or-</span></span>  
  
1. <span data-ttu-id="b7809-120">本機變數中，放置`Dim`程序內變數的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="b7809-121">不包含`Public`中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="b7809-122">您可以讀取或寫入變數，從程序中的任何位置，而不是從其外部。</span><span class="sxs-lookup"><span data-stu-id="b7809-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="b7809-123">受保護和 Friend 存取權限</span><span class="sxs-lookup"><span data-stu-id="b7809-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="b7809-124">您可以限制變數對其類別和衍生的類別，或其組件的存取層級。</span><span class="sxs-lookup"><span data-stu-id="b7809-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="b7809-125">您也可以指定這些限制，可讓您從程式碼的存取相同的組件中的任何其他位置或任何衍生類別中的聯集。</span><span class="sxs-lookup"><span data-stu-id="b7809-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="b7809-126">您指定這個聯集結合`Protected`和`Friend`相同宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b7809-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="b7809-127">若要在其類別和任何衍生的類別內只能從存取變數</span><span class="sxs-lookup"><span data-stu-id="b7809-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="b7809-128">位置`Dim`陳述式的類別，但任何程序之外的變數。</span><span class="sxs-lookup"><span data-stu-id="b7809-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="b7809-129">包含[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="b7809-130">您可以讀取或寫入變數，從任何地方在類別中，以及從任何類別衍生，而不是從衍生鏈結中的任何類別外部。</span><span class="sxs-lookup"><span data-stu-id="b7809-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="b7809-131">若要只能從相同的組件中存取變數</span><span class="sxs-lookup"><span data-stu-id="b7809-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="b7809-132">位置`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="b7809-133">包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="b7809-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="b7809-134">您可以讀取或寫入變數，從模組、 類別或結構內的任何位置，以及從任何程式碼位於相同的組件，而不是從外部組件。</span><span class="sxs-lookup"><span data-stu-id="b7809-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7809-135">範例</span><span class="sxs-lookup"><span data-stu-id="b7809-135">Example</span></span>  
 <span data-ttu-id="b7809-136">下列範例顯示的變數宣告`Public`， `Protected`， `Friend`， `Protected Friend`，和`Private`存取層級。</span><span class="sxs-lookup"><span data-stu-id="b7809-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="b7809-137">請注意，當`Dim`陳述式會指定存取層級，您不需要包含`Dim`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b7809-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="b7809-138">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b7809-138">.NET Framework Security</span></span>  
 <span data-ttu-id="b7809-139">更嚴格變數的存取層級，它使用較小的機會，惡意程式碼不適當。</span><span class="sxs-lookup"><span data-stu-id="b7809-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7809-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7809-140">See also</span></span>

- [<span data-ttu-id="b7809-141">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="b7809-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b7809-142">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="b7809-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="b7809-143">Public</span><span class="sxs-lookup"><span data-stu-id="b7809-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="b7809-144">Protected</span><span class="sxs-lookup"><span data-stu-id="b7809-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="b7809-145">Friend</span><span class="sxs-lookup"><span data-stu-id="b7809-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="b7809-146">Private</span><span class="sxs-lookup"><span data-stu-id="b7809-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
