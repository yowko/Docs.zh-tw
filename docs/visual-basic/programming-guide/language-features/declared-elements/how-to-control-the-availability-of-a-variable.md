---
title: 如何：控制變數的可用性
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
ms.openlocfilehash: 0bfa7fa2bdac4746827884c1dad62734c549a48e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357383"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="eb473-102">如何：控制變數的可用性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb473-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="eb473-103">您可以藉由指定其*存取層級*來控制變數的可用性。</span><span class="sxs-lookup"><span data-stu-id="eb473-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="eb473-104">存取層級會決定哪些程式碼有權讀取或寫入變數。</span><span class="sxs-lookup"><span data-stu-id="eb473-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
- <span data-ttu-id="eb473-105">*成員變數*（定義于模組層級和在任何程式之外）預設為公用存取，這表示任何可查看它們的程式碼都可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="eb473-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="eb473-106">您可以藉由指定存取修飾詞來變更此項。</span><span class="sxs-lookup"><span data-stu-id="eb473-106">You can change this by specifying an access modifier.</span></span>  
  
- <span data-ttu-id="eb473-107">*本機變數*（在程式內定義）名義上具有公用存取權，雖然只有其程式中的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="eb473-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="eb473-108">您不能變更本機變數的存取層級，但是可以變更包含它之程式的存取層級。</span><span class="sxs-lookup"><span data-stu-id="eb473-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="eb473-109">如需詳細資訊，請參閱[Visual Basic 中的存取層級](access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="eb473-109">For more information, see [Access levels in Visual Basic](access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="eb473-110">私用和公用存取</span><span class="sxs-lookup"><span data-stu-id="eb473-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="eb473-111">讓只能從其模組、類別或結構中存取的變數</span><span class="sxs-lookup"><span data-stu-id="eb473-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1. <span data-ttu-id="eb473-112">將變數的[Dim 語句](../../../language-reference/statements/dim-statement.md)放在模組、類別或結構中，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="eb473-112">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="eb473-113">在語句中包含[Private](../../../language-reference/modifiers/private.md)關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-113">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="eb473-114">您可以從模組、類別或結構內的任何位置讀取或寫入變數，而不是從外部進行。</span><span class="sxs-lookup"><span data-stu-id="eb473-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="eb473-115">若要讓變數可以從任何可看到的程式碼存取</span><span class="sxs-lookup"><span data-stu-id="eb473-115">To make a variable accessible from any code that can see it</span></span>  
  
1. <span data-ttu-id="eb473-116">對於成員變數，請將變數的語句放在 `Dim` 模組、類別或結構中，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="eb473-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="eb473-117">在語句中包含[Public](../../../language-reference/modifiers/public.md)關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-117">Include the [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="eb473-118">您可以從任何與您的元件互通的程式碼中讀取或寫入變數。</span><span class="sxs-lookup"><span data-stu-id="eb473-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="eb473-119">-或-</span><span class="sxs-lookup"><span data-stu-id="eb473-119">-or-</span></span>  
  
1. <span data-ttu-id="eb473-120">針對本機變數，請將變數的語句放在程式 `Dim` 內。</span><span class="sxs-lookup"><span data-stu-id="eb473-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2. <span data-ttu-id="eb473-121">請勿 `Public` 在語句中包含關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="eb473-122">您可以從程式內的任何位置讀取或寫入變數，而不是從外部進行。</span><span class="sxs-lookup"><span data-stu-id="eb473-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="eb473-123">受保護和 Friend 存取</span><span class="sxs-lookup"><span data-stu-id="eb473-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="eb473-124">您可以將變數的存取層級限制為其類別和任何衍生類別，或其元件。</span><span class="sxs-lookup"><span data-stu-id="eb473-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="eb473-125">您也可以指定這些限制的聯集，允許從任何衍生類別中的程式碼，或在相同元件中的任何其他位置進行存取。</span><span class="sxs-lookup"><span data-stu-id="eb473-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="eb473-126">您可以在相同的宣告中結合和關鍵字來指定這個聯集 `Protected` `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="eb473-127">使變數只能從其類別和任何衍生類別中存取</span><span class="sxs-lookup"><span data-stu-id="eb473-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1. <span data-ttu-id="eb473-128">將變數的語句放在 `Dim` 類別內，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="eb473-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="eb473-129">在語句中包含[Protected](../../../language-reference/modifiers/protected.md)關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-129">Include the [Protected](../../../language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="eb473-130">您可以從類別內的任何位置讀取或寫入變數，以及從任何衍生自它的類別內，而不是從衍生鏈中的任何類別之外。</span><span class="sxs-lookup"><span data-stu-id="eb473-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="eb473-131">使變數只能從相同的元件中存取</span><span class="sxs-lookup"><span data-stu-id="eb473-131">To make a variable accessible only from within the same assembly</span></span>  
  
1. <span data-ttu-id="eb473-132">將變數的語句放在 `Dim` 模組、類別或結構中，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="eb473-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="eb473-133">在語句中包含[Friend](../../../language-reference/modifiers/friend.md)關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="eb473-133">Include the [Friend](../../../language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="eb473-134">您可以從模組、類別或結構內的任何位置讀取或寫入變數，以及從相同元件中的任何程式碼，而不是從元件外部進行讀取或寫入。</span><span class="sxs-lookup"><span data-stu-id="eb473-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb473-135">範例</span><span class="sxs-lookup"><span data-stu-id="eb473-135">Example</span></span>  
 <span data-ttu-id="eb473-136">下列範例顯示具有 `Public` 、 `Protected` 、 `Friend` 、 `Protected Friend` 和 `Private` 存取層級的變數宣告。</span><span class="sxs-lookup"><span data-stu-id="eb473-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="eb473-137">請注意，當 `Dim` 語句指定存取層級時，您不需要包含 `Dim` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eb473-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="eb473-138">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="eb473-138">.NET Framework Security</span></span>  
 <span data-ttu-id="eb473-139">變數的存取層級越嚴格，惡意程式碼就越有可能不適當地使用它。</span><span class="sxs-lookup"><span data-stu-id="eb473-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb473-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb473-140">See also</span></span>

- [<span data-ttu-id="eb473-141">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="eb473-141">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="eb473-142">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="eb473-142">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
- [<span data-ttu-id="eb473-143">公開</span><span class="sxs-lookup"><span data-stu-id="eb473-143">Public</span></span>](../../../language-reference/modifiers/public.md)
- [<span data-ttu-id="eb473-144">免受</span><span class="sxs-lookup"><span data-stu-id="eb473-144">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="eb473-145">給</span><span class="sxs-lookup"><span data-stu-id="eb473-145">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="eb473-146">私用</span><span class="sxs-lookup"><span data-stu-id="eb473-146">Private</span></span>](../../../language-reference/modifiers/private.md)
