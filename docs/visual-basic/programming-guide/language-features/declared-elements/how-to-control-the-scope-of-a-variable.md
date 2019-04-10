---
title: HOW TO：控制的範圍變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 24a7ae3b8f3400beeaedb20ea6352ea44bdb7597
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324314"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="2de3c-102">HOW TO：控制的範圍變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2de3c-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="2de3c-103">一般而言，變數會處於*範圍*，或顯示供您參考，在宣告它的區域。</span><span class="sxs-lookup"><span data-stu-id="2de3c-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="2de3c-104">在某些情況下，變數的*存取層級*可能會影響其範圍。</span><span class="sxs-lookup"><span data-stu-id="2de3c-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="2de3c-105">如需詳細資訊，請參閱 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="2de3c-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="2de3c-106">在區塊或程序層級的範圍</span><span class="sxs-lookup"><span data-stu-id="2de3c-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="2de3c-107">若要將變數的區塊內才可見</span><span class="sxs-lookup"><span data-stu-id="2de3c-107">To make a variable visible only within a block</span></span>  
  
-   <span data-ttu-id="2de3c-108">地方[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)之間的初始和之間，例如終止宣告陳述式，該區塊中，變數`For`並`Next`陳述式的`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="2de3c-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="2de3c-109">您可以參考此變數只在區塊內。</span><span class="sxs-lookup"><span data-stu-id="2de3c-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="2de3c-110">若要在程序內才可見變數</span><span class="sxs-lookup"><span data-stu-id="2de3c-110">To make a variable visible only within a procedure</span></span>  
  
-   <span data-ttu-id="2de3c-111">地方`Dim`程序內，但任何區塊外部變數的陳述式 (例如`With`...`End With`區塊)。</span><span class="sxs-lookup"><span data-stu-id="2de3c-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="2de3c-112">您可以參考此變數只會從程序，包括任何程序中所含的區塊內。</span><span class="sxs-lookup"><span data-stu-id="2de3c-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="2de3c-113">在模組或命名空間層級的範圍</span><span class="sxs-lookup"><span data-stu-id="2de3c-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="2de3c-114">為了方便起見，單一詞彙*模組層級*同樣適用於模組、 類別和結構。</span><span class="sxs-lookup"><span data-stu-id="2de3c-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="2de3c-115">模組層級變數的存取層級會決定其範圍。</span><span class="sxs-lookup"><span data-stu-id="2de3c-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="2de3c-116">包含模組、 類別或結構的命名空間也會影響範圍。</span><span class="sxs-lookup"><span data-stu-id="2de3c-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="2de3c-117">若要顯示在整個模組、 類別或結構變數</span><span class="sxs-lookup"><span data-stu-id="2de3c-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="2de3c-118">位置`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2de3c-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="2de3c-119">包含[私人](../../../../visual-basic/language-reference/modifiers/private.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="2de3c-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="2de3c-120">您可以參考變數，從模組、 類別或結構內的任何位置，而不是從其外部。</span><span class="sxs-lookup"><span data-stu-id="2de3c-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="2de3c-121">若要顯示整個命名空間變數</span><span class="sxs-lookup"><span data-stu-id="2de3c-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="2de3c-122">位置`Dim`變數內模組、 類別或結構，但以外的任何程序的陳述式。</span><span class="sxs-lookup"><span data-stu-id="2de3c-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="2de3c-123">包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或是[公用](../../../../visual-basic/language-reference/modifiers/public.md)中的關鍵字`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="2de3c-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="2de3c-124">您可以從任何位置參考此變數包含模組、 類別或結構的命名空間內。</span><span class="sxs-lookup"><span data-stu-id="2de3c-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2de3c-125">範例</span><span class="sxs-lookup"><span data-stu-id="2de3c-125">Example</span></span>  
 <span data-ttu-id="2de3c-126">下列範例會宣告一個變數，在模組層級，並限制其可見性的模組中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2de3c-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="2de3c-127">在上述範例中，所有的程序則是在模組中定義`demonstrateScope`可以參考`String`變數`strMsg`。</span><span class="sxs-lookup"><span data-stu-id="2de3c-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="2de3c-128">當`usePrivateVariable`呼叫程序，它會顯示字串變數的內容`strMsg`在對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="2de3c-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="2de3c-129">使用上述範例中，字串變數將`strMsg`可以由其宣告的命名空間中的任何位置的程式碼加以參考。</span><span class="sxs-lookup"><span data-stu-id="2de3c-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="2de3c-130">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2de3c-130">Robust Programming</span></span>  
 <span data-ttu-id="2de3c-131">範圍愈小的變數中，您有適用於不小心參考它來取代另一個變數具有相同名稱的機會。</span><span class="sxs-lookup"><span data-stu-id="2de3c-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="2de3c-132">您也可以減少參考相符的問題。</span><span class="sxs-lookup"><span data-stu-id="2de3c-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2de3c-133">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="2de3c-133">.NET Framework Security</span></span>  
 <span data-ttu-id="2de3c-134">變數的範圍越小的機會，惡意程式碼不適當使用它。</span><span class="sxs-lookup"><span data-stu-id="2de3c-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de3c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2de3c-135">See also</span></span>

- [<span data-ttu-id="2de3c-136">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="2de3c-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="2de3c-137">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="2de3c-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="2de3c-138">在 Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="2de3c-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2de3c-139">變數</span><span class="sxs-lookup"><span data-stu-id="2de3c-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="2de3c-140">變數宣告</span><span class="sxs-lookup"><span data-stu-id="2de3c-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="2de3c-141">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="2de3c-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
