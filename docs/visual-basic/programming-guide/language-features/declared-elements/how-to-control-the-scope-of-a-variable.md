---
title: 如何：控制變數的範圍
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
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345382"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="92784-102">如何：控制變數的範圍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92784-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>
<span data-ttu-id="92784-103">一般來說，變數會在您宣告它的整個區域中，在*範圍*內，或可見以供參考。</span><span class="sxs-lookup"><span data-stu-id="92784-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="92784-104">在某些情況下，變數的*存取層級*可能會影響其範圍。</span><span class="sxs-lookup"><span data-stu-id="92784-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="92784-105">如需詳細資訊，請參閱 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="92784-105">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="92784-106">區塊或程式層級的範圍</span><span class="sxs-lookup"><span data-stu-id="92784-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="92784-107">使變數只在區塊內可見</span><span class="sxs-lookup"><span data-stu-id="92784-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="92784-108">將變數的[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)放在該區塊的起始和結束宣告語句之間，例如，在 `For` 迴圈的 `For` 和 `Next` 語句之間。</span><span class="sxs-lookup"><span data-stu-id="92784-108">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="92784-109">您只能從區塊內參考該變數。</span><span class="sxs-lookup"><span data-stu-id="92784-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="92784-110">使變數只在程式內可見</span><span class="sxs-lookup"><span data-stu-id="92784-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="92784-111">將變數的 `Dim` 語句放在程式內，但不在任何區塊（例如 `With`...`End With` 區塊）的外部。</span><span class="sxs-lookup"><span data-stu-id="92784-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="92784-112">您只能從程式內參考變數，包括程式中包含的任何區塊內。</span><span class="sxs-lookup"><span data-stu-id="92784-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="92784-113">模組或命名空間層級的範圍</span><span class="sxs-lookup"><span data-stu-id="92784-113">Scope at Module or Namespace Level</span></span>  
 <span data-ttu-id="92784-114">為了方便起見，單一詞彙*模組層級*同樣適用于模組、類別和結構。</span><span class="sxs-lookup"><span data-stu-id="92784-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="92784-115">模組層級變數的存取層級會決定其範圍。</span><span class="sxs-lookup"><span data-stu-id="92784-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="92784-116">包含模組、類別或結構的命名空間也會影響範圍。</span><span class="sxs-lookup"><span data-stu-id="92784-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="92784-117">若要讓變數在整個模組、類別或結構中可見</span><span class="sxs-lookup"><span data-stu-id="92784-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="92784-118">將變數的 `Dim` 語句放在模組、類別或結構中，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="92784-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="92784-119">在 `Dim` 語句中包含[Private](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="92784-119">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="92784-120">您可以從模組、類別或結構中的任何位置參考該變數，而不是從外部。</span><span class="sxs-lookup"><span data-stu-id="92784-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="92784-121">若要讓變數在整個命名空間中可見</span><span class="sxs-lookup"><span data-stu-id="92784-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="92784-122">將變數的 `Dim` 語句放在模組、類別或結構中，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="92784-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="92784-123">在 `Dim` 語句中包含[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Public](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="92784-123">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="92784-124">您可以從包含模組、類別或結構之命名空間內的任何位置參考該變數。</span><span class="sxs-lookup"><span data-stu-id="92784-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92784-125">範例</span><span class="sxs-lookup"><span data-stu-id="92784-125">Example</span></span>  
 <span data-ttu-id="92784-126">下列範例會在模組層級宣告變數，並限制其對模組內程式碼的可見度。</span><span class="sxs-lookup"><span data-stu-id="92784-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="92784-127">在上述範例中，模組 `demonstrateScope` 中定義的所有程式都可以參考 `String` 變數 `strMsg`。</span><span class="sxs-lookup"><span data-stu-id="92784-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="92784-128">呼叫 `usePrivateVariable` 程式時，會在對話方塊中顯示字串變數 `strMsg` 的內容。</span><span class="sxs-lookup"><span data-stu-id="92784-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="92784-129">在上述範例中的下列改變之後，字串變數 `strMsg` 可以在其宣告之命名空間中的任何位置參考。</span><span class="sxs-lookup"><span data-stu-id="92784-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="92784-130">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="92784-130">Robust Programming</span></span>  
 <span data-ttu-id="92784-131">變數的範圍越窄，您就不小心參考它來取代另一個具有相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="92784-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="92784-132">您也可以將參考比對的問題降至最低。</span><span class="sxs-lookup"><span data-stu-id="92784-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="92784-133">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="92784-133">.NET Framework Security</span></span>  
 <span data-ttu-id="92784-134">變數的範圍愈窄，惡意程式碼可能不適當地使用它的機率就愈小。</span><span class="sxs-lookup"><span data-stu-id="92784-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92784-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="92784-135">See also</span></span>

- [<span data-ttu-id="92784-136">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="92784-136">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="92784-137">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="92784-137">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="92784-138">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="92784-138">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="92784-139">變數</span><span class="sxs-lookup"><span data-stu-id="92784-139">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="92784-140">變數宣告</span><span class="sxs-lookup"><span data-stu-id="92784-140">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="92784-141">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="92784-141">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
