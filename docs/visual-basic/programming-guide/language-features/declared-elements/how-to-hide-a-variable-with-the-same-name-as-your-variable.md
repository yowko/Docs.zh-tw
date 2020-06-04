---
title: 如何：隱藏與您的變數名稱相同的變數
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: c1f4c2fbf339358be77e76468b1db94616bf04a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357228"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="f2e93-102">如何：隱藏與您的變數名稱相同的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2e93-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="f2e93-103">您可以藉由將變數*遮蔽*來加以隱藏，也就是使用相同名稱的變數重新加以定義。</span><span class="sxs-lookup"><span data-stu-id="f2e93-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="f2e93-104">您可以透過兩種方式遮蔽要隱藏的變數：</span><span class="sxs-lookup"><span data-stu-id="f2e93-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="f2e93-105">**透過範圍遮蔽。**</span><span class="sxs-lookup"><span data-stu-id="f2e93-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="f2e93-106">您可以透過範圍來遮蔽它，方法是在包含您要隱藏之變數的區域的子領域內重新宣告它。</span><span class="sxs-lookup"><span data-stu-id="f2e93-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="f2e93-107">**透過繼承進行遮蔽。**</span><span class="sxs-lookup"><span data-stu-id="f2e93-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="f2e93-108">如果您要隱藏的變數是在類別層級定義的，您可以在衍生類別中使用[Shadows](../../../language-reference/modifiers/shadows.md)關鍵字重新宣告，藉以透過繼承來遮蔽它。</span><span class="sxs-lookup"><span data-stu-id="f2e93-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="f2e93-109">隱藏變數的兩種方式</span><span class="sxs-lookup"><span data-stu-id="f2e93-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="f2e93-110">藉由在範圍內遮蔽來隱藏變數</span><span class="sxs-lookup"><span data-stu-id="f2e93-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="f2e93-111">判斷定義您想要隱藏之變數的區域，並決定要在其中使用變數重新定義的子領域。</span><span class="sxs-lookup"><span data-stu-id="f2e93-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="f2e93-112">變數的區域</span><span class="sxs-lookup"><span data-stu-id="f2e93-112">Variable's region</span></span>|<span data-ttu-id="f2e93-113">用於重新定義它的允許子領域</span><span class="sxs-lookup"><span data-stu-id="f2e93-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="f2e93-114">模組</span><span class="sxs-lookup"><span data-stu-id="f2e93-114">Module</span></span>|<span data-ttu-id="f2e93-115">模組中的類別</span><span class="sxs-lookup"><span data-stu-id="f2e93-115">A class within the module</span></span>|
    |<span data-ttu-id="f2e93-116">類別</span><span class="sxs-lookup"><span data-stu-id="f2e93-116">Class</span></span>|<span data-ttu-id="f2e93-117">類別內的子類別</span><span class="sxs-lookup"><span data-stu-id="f2e93-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="f2e93-118">類別中的程式</span><span class="sxs-lookup"><span data-stu-id="f2e93-118">A procedure within the class</span></span>|

    <span data-ttu-id="f2e93-119">您不能在該程式內的區塊中重新定義過程變數，例如在 `If` ... `End If` 結構或 `For` 迴圈中。</span><span class="sxs-lookup"><span data-stu-id="f2e93-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="f2e93-120">建立子領域（如果尚未存在的話）。</span><span class="sxs-lookup"><span data-stu-id="f2e93-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="f2e93-121">在子領域內，撰寫用來宣告遮蔽變數的[Dim 語句](../../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e93-121">Within the subregion, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="f2e93-122">當子領域內的程式碼參考變數名稱時，編譯器會解析遮蔽變數的參考。</span><span class="sxs-lookup"><span data-stu-id="f2e93-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="f2e93-123">下列範例說明如何透過範圍進行遮蔽，以及略過遮蔽的參考。</span><span class="sxs-lookup"><span data-stu-id="f2e93-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    <span data-ttu-id="f2e93-124">上述範例會 `num` 在模組層級和程式層級宣告變數（在程式中 `show` ）。</span><span class="sxs-lookup"><span data-stu-id="f2e93-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="f2e93-125">區域變數 `num` 會遮蔽中的模組層級變數 `num` `show` ，所以區域變數會設定為2。</span><span class="sxs-lookup"><span data-stu-id="f2e93-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="f2e93-126">不過，程式中沒有可遮蔽的本機變數 `num` `useModuleLevelNum` 。</span><span class="sxs-lookup"><span data-stu-id="f2e93-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="f2e93-127">因此，會 `useModuleLevelNum` 將模組層級變數的值設定為1。</span><span class="sxs-lookup"><span data-stu-id="f2e93-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="f2e93-128">內部的呼叫會透過 `MsgBox` `show` `num` 以模組名稱限定來略過遮蔽的機制。</span><span class="sxs-lookup"><span data-stu-id="f2e93-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="f2e93-129">因此，它會顯示模組層級變數，而不是本機變數。</span><span class="sxs-lookup"><span data-stu-id="f2e93-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="f2e93-130">藉由透過繼承來遮蔽變數以加以隱藏</span><span class="sxs-lookup"><span data-stu-id="f2e93-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="f2e93-131">請確定您要隱藏的變數是在類別中宣告，而在類別層級（在任何程式之外）宣告。</span><span class="sxs-lookup"><span data-stu-id="f2e93-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="f2e93-132">否則，您就無法透過繼承來遮蔽它。</span><span class="sxs-lookup"><span data-stu-id="f2e93-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="f2e93-133">定義衍生引數類別的類別（如果尚未存在的話）。</span><span class="sxs-lookup"><span data-stu-id="f2e93-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="f2e93-134">在衍生類別中，撰寫宣告 `Dim` 變數的語句。</span><span class="sxs-lookup"><span data-stu-id="f2e93-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="f2e93-135">在宣告中包含[Shadows](../../../language-reference/modifiers/shadows.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f2e93-135">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="f2e93-136">當衍生類別中的程式碼參考變數名稱時，編譯器會解析變數的參考。</span><span class="sxs-lookup"><span data-stu-id="f2e93-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="f2e93-137">下列範例說明透過繼承的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="f2e93-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="f2e93-138">它會建立兩個參考，一個存取遮蔽變數，另一個則會略過遮蔽。</span><span class="sxs-lookup"><span data-stu-id="f2e93-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="f2e93-139">上述範例 `shadowString` 會在基類中宣告變數，並將其遮蔽在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="f2e93-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="f2e93-140">`showStrings`當名稱未限定時，衍生類別中的程式會顯示字串的遮蔽版本 `shadowString` 。</span><span class="sxs-lookup"><span data-stu-id="f2e93-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="f2e93-141">然後，它 `shadowString` 會在以關鍵字限定時顯示陰影版本 `MyBase` 。</span><span class="sxs-lookup"><span data-stu-id="f2e93-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="f2e93-142">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f2e93-142">Robust Programming</span></span>

<span data-ttu-id="f2e93-143">遮蔽導入了一個以上具有相同名稱的變數版本。</span><span class="sxs-lookup"><span data-stu-id="f2e93-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="f2e93-144">當程式碼語句參考變數名稱時，編譯器解析參考的目標版本取決於程式碼語句的位置，以及符合資格的字串是否存在等因素。</span><span class="sxs-lookup"><span data-stu-id="f2e93-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="f2e93-145">這可能會增加參考非預期版本的陰影變數的風險。</span><span class="sxs-lookup"><span data-stu-id="f2e93-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="f2e93-146">您可以藉由完整限定遮蔽變數的所有參考，來降低風險。</span><span class="sxs-lookup"><span data-stu-id="f2e93-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2e93-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2e93-147">See also</span></span>

- [<span data-ttu-id="f2e93-148">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="f2e93-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="f2e93-149">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="f2e93-149">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="f2e93-150">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="f2e93-150">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="f2e93-151">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="f2e93-151">How to: Hide an Inherited Variable</span></span>](how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="f2e93-152">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="f2e93-152">How to: Access a Variable Hidden by a Derived Class</span></span>](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="f2e93-153">覆寫</span><span class="sxs-lookup"><span data-stu-id="f2e93-153">Overrides</span></span>](../../../language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f2e93-154">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="f2e93-154">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f2e93-155">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="f2e93-155">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
