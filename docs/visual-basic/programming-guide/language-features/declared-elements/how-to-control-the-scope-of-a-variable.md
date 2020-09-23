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
ms.openlocfilehash: 2ce7c1700eec54542719e6e0880466ca136e86f6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095429"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a><span data-ttu-id="1801b-102">如何：控制變數的範圍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1801b-102">How to: Control the Scope of a Variable (Visual Basic)</span></span>

<span data-ttu-id="1801b-103">一般情況下，變數會在您宣告的區域中，于 *範圍*內或可供參考。</span><span class="sxs-lookup"><span data-stu-id="1801b-103">Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it.</span></span> <span data-ttu-id="1801b-104">在某些情況下，變數的 *存取層級* 可能會影響其範圍。</span><span class="sxs-lookup"><span data-stu-id="1801b-104">In some cases, the variable's *access level* can influence its scope.</span></span>  
  
 <span data-ttu-id="1801b-105">如需詳細資訊，請參閱 [Scope in Visual Basic](scope.md)。</span><span class="sxs-lookup"><span data-stu-id="1801b-105">For more information, see [Scope in Visual Basic](scope.md).</span></span>  
  
## <a name="scope-at-block-or-procedure-level"></a><span data-ttu-id="1801b-106">區塊或程式層級的範圍</span><span class="sxs-lookup"><span data-stu-id="1801b-106">Scope at Block or Procedure Level</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a><span data-ttu-id="1801b-107">讓變數只在區塊內可見</span><span class="sxs-lookup"><span data-stu-id="1801b-107">To make a variable visible only within a block</span></span>  
  
- <span data-ttu-id="1801b-108">在該區塊的起始和終止宣告語句之間放置變數的 [Dim 語句](../../../language-reference/statements/dim-statement.md) ，例如在 `For` 迴圈的和語句之間 `Next` `For` 。</span><span class="sxs-lookup"><span data-stu-id="1801b-108">Place the [Dim Statement](../../../language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.</span></span>  
  
     <span data-ttu-id="1801b-109">您只能從區塊內參考該變數。</span><span class="sxs-lookup"><span data-stu-id="1801b-109">You can refer to the variable only from within the block.</span></span>  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a><span data-ttu-id="1801b-110">讓變數只在程式中顯示</span><span class="sxs-lookup"><span data-stu-id="1801b-110">To make a variable visible only within a procedure</span></span>  
  
- <span data-ttu-id="1801b-111">將變數的語句放在程式 `Dim` 內，但在任何區塊 (（例如 `With` ... `End With` block) ）之外。</span><span class="sxs-lookup"><span data-stu-id="1801b-111">Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).</span></span>  
  
     <span data-ttu-id="1801b-112">您只能從程式內（包括程式中包含的任何區塊內）參考該變數。</span><span class="sxs-lookup"><span data-stu-id="1801b-112">You can refer to the variable only from within the procedure, including inside any block contained in the procedure.</span></span>  
  
## <a name="scope-at-module-or-namespace-level"></a><span data-ttu-id="1801b-113">模組或命名空間層級的範圍</span><span class="sxs-lookup"><span data-stu-id="1801b-113">Scope at Module or Namespace Level</span></span>  

 <span data-ttu-id="1801b-114">為了方便起見，單一詞彙 *模組層級* 同樣適用于模組、類別和結構。</span><span class="sxs-lookup"><span data-stu-id="1801b-114">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="1801b-115">模組層級變數的存取層級會決定其範圍。</span><span class="sxs-lookup"><span data-stu-id="1801b-115">The access level of a module level variable determines its scope.</span></span> <span data-ttu-id="1801b-116">包含模組、類別或結構的命名空間也會影響範圍。</span><span class="sxs-lookup"><span data-stu-id="1801b-116">The namespace that contains the module, class, or structure also influences the scope.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a><span data-ttu-id="1801b-117">讓變數在整個模組、類別或結構中都可見</span><span class="sxs-lookup"><span data-stu-id="1801b-117">To make a variable visible throughout a module, class, or structure</span></span>  
  
1. <span data-ttu-id="1801b-118">將變數的語句放在 `Dim` 模組、類別或結構內，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="1801b-118">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="1801b-119">在語句中包含 [私](../../../language-reference/modifiers/private.md) 用關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="1801b-119">Include the [Private](../../../language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="1801b-120">您可以從模組、類別或結構內的任何位置參考變數，但不能從外部參考該變數。</span><span class="sxs-lookup"><span data-stu-id="1801b-120">You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a><span data-ttu-id="1801b-121">讓變數在命名空間中可見</span><span class="sxs-lookup"><span data-stu-id="1801b-121">To make a variable visible throughout a namespace</span></span>  
  
1. <span data-ttu-id="1801b-122">將變數的語句放在 `Dim` 模組、類別或結構內，但在任何程式之外。</span><span class="sxs-lookup"><span data-stu-id="1801b-122">Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2. <span data-ttu-id="1801b-123">在語句中包含 [Friend](../../../language-reference/modifiers/friend.md) 或 [Public](../../../language-reference/modifiers/public.md) 關鍵字 `Dim` 。</span><span class="sxs-lookup"><span data-stu-id="1801b-123">Include the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
3. <span data-ttu-id="1801b-124">您可以從包含模組、類別或結構的命名空間中的任何位置參考變數。</span><span class="sxs-lookup"><span data-stu-id="1801b-124">You can refer to the variable from anywhere within the namespace containing the module, class, or structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1801b-125">範例</span><span class="sxs-lookup"><span data-stu-id="1801b-125">Example</span></span>  

 <span data-ttu-id="1801b-126">下列範例會在模組層級宣告變數，並限制其在模組內的程式碼可見度。</span><span class="sxs-lookup"><span data-stu-id="1801b-126">The following example declares a variable at module level and limits its visibility to code within the module.</span></span>  
  
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
  
 <span data-ttu-id="1801b-127">在上述範例中，模組中定義的所有程式都 `demonstrateScope` 可以參考 `String` 變數 `strMsg` 。</span><span class="sxs-lookup"><span data-stu-id="1801b-127">In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`.</span></span> <span data-ttu-id="1801b-128">`usePrivateVariable`呼叫程式時，它會在對話方塊中顯示字串變數的內容 `strMsg` 。</span><span class="sxs-lookup"><span data-stu-id="1801b-128">When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
 <span data-ttu-id="1801b-129">使用上述範例中的下列變更，可以在其宣告的 `strMsg` 命名空間中的任何位置，將字串變數參考至程式碼。</span><span class="sxs-lookup"><span data-stu-id="1801b-129">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a><span data-ttu-id="1801b-130">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1801b-130">Robust Programming</span></span>  

 <span data-ttu-id="1801b-131">變數的範圍愈窄，您所擁有的機會不會被用來取代另一個具有相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="1801b-131">The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name.</span></span> <span data-ttu-id="1801b-132">您也可以將參考比對的問題降至最低。</span><span class="sxs-lookup"><span data-stu-id="1801b-132">You can also minimize problems of reference matching.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1801b-133">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1801b-133">.NET Framework Security</span></span>  

 <span data-ttu-id="1801b-134">變數的範圍愈窄，惡意程式碼可能不當使用它的機率就愈小。</span><span class="sxs-lookup"><span data-stu-id="1801b-134">The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1801b-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1801b-135">See also</span></span>

- [<span data-ttu-id="1801b-136">Visual Basic 中的範圍</span><span class="sxs-lookup"><span data-stu-id="1801b-136">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="1801b-137">Visual Basic 中的存留期</span><span class="sxs-lookup"><span data-stu-id="1801b-137">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="1801b-138">Visual Basic 中的存取層級</span><span class="sxs-lookup"><span data-stu-id="1801b-138">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="1801b-139">變數</span><span class="sxs-lookup"><span data-stu-id="1801b-139">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="1801b-140">變數宣告</span><span class="sxs-lookup"><span data-stu-id="1801b-140">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="1801b-141">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="1801b-141">Dim Statement</span></span>](../../../language-reference/statements/dim-statement.md)
