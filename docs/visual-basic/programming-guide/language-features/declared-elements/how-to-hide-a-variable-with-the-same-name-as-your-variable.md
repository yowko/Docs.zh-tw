---
title: HOW TO：隱藏與您的變數 (Visual Basic) 同名的變數
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
ms.openlocfilehash: a8a7eda2a636d7f89131d140c82ad4f3c4743211
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826674"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="c548b-102">HOW TO：隱藏與您的變數 (Visual Basic) 同名的變數</span><span class="sxs-lookup"><span data-stu-id="c548b-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>
<span data-ttu-id="c548b-103">您可以隱藏變數*遮蔽*它，也就是藉由重新定義它，以相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="c548b-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="c548b-104">您可以遮蔽您想要隱藏有兩種的變數：</span><span class="sxs-lookup"><span data-stu-id="c548b-104">You can shadow the variable you want to hide in two ways:</span></span>  
  
-   <span data-ttu-id="c548b-105">**透過範圍遮蔽。**</span><span class="sxs-lookup"><span data-stu-id="c548b-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="c548b-106">您可以透過範圍遮蔽它的宣告包含您想要隱藏的變數的區域的子區域內。</span><span class="sxs-lookup"><span data-stu-id="c548b-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>  
  
-   <span data-ttu-id="c548b-107">**透過繼承遮蔽。**</span><span class="sxs-lookup"><span data-stu-id="c548b-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="c548b-108">如果您想要隱藏的變數定義在類別層級，您可以透過繼承來遮蔽藉由宣告它與[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)衍生類別中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c548b-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>  
  
## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="c548b-109">若要隱藏變數的兩種方式</span><span class="sxs-lookup"><span data-stu-id="c548b-109">Two Ways to Hide a Variable</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="c548b-110">若要隱藏的變數，來透過範圍遮蔽</span><span class="sxs-lookup"><span data-stu-id="c548b-110">To hide a variable by shadowing it through scope</span></span>  
  
1.  <span data-ttu-id="c548b-111">判斷區域定義您想要隱藏此項目，該的變數，並判斷要在其中以您的變數重新定義它的子區域。</span><span class="sxs-lookup"><span data-stu-id="c548b-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>  
  
    |<span data-ttu-id="c548b-112">變數的區域</span><span class="sxs-lookup"><span data-stu-id="c548b-112">Variable's region</span></span>|<span data-ttu-id="c548b-113">重新定義它的可允許子區域</span><span class="sxs-lookup"><span data-stu-id="c548b-113">Allowable subregion for redefining it</span></span>|  
    |-----------------------|-------------------------------------------|  
    |<span data-ttu-id="c548b-114">Module</span><span class="sxs-lookup"><span data-stu-id="c548b-114">Module</span></span>|<span data-ttu-id="c548b-115">在模組中的類別</span><span class="sxs-lookup"><span data-stu-id="c548b-115">A class within the module</span></span>|  
    |<span data-ttu-id="c548b-116">類別</span><span class="sxs-lookup"><span data-stu-id="c548b-116">Class</span></span>|<span data-ttu-id="c548b-117">在類別內的子類別</span><span class="sxs-lookup"><span data-stu-id="c548b-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="c548b-118">在類別中的程序</span><span class="sxs-lookup"><span data-stu-id="c548b-118">A procedure within the class</span></span>|  
  
     <span data-ttu-id="c548b-119">您無法重新定義程序變數的區塊中的程序中，例如在`If`...`End If`建構或`For`迴圈。</span><span class="sxs-lookup"><span data-stu-id="c548b-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>  
  
2.  <span data-ttu-id="c548b-120">如果不存在，請予以建立。</span><span class="sxs-lookup"><span data-stu-id="c548b-120">Create the subregion if it does not already exist.</span></span>  
  
3.  <span data-ttu-id="c548b-121">在子區域中，撰寫[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)遮蔽變數宣告。</span><span class="sxs-lookup"><span data-stu-id="c548b-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>  
  
     <span data-ttu-id="c548b-122">當子區域內的程式碼會參考變數的名稱時，編譯器會解析遮蔽變數的參考。</span><span class="sxs-lookup"><span data-stu-id="c548b-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>  
  
     <span data-ttu-id="c548b-123">下列範例示範如何透過範圍，以及略過遮蔽的參考遮蔽。</span><span class="sxs-lookup"><span data-stu-id="c548b-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="c548b-124">上述範例中宣告變數`num`在模組層級和程序層級 (在程序`show`)。</span><span class="sxs-lookup"><span data-stu-id="c548b-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="c548b-125">區域變數`num`遮蔽模組層級變數`num`內`show`，因此本機變數設為 2。</span><span class="sxs-lookup"><span data-stu-id="c548b-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="c548b-126">不過，沒有任何本機變數，以遮蔽`num`在`useModuleLevelNum`程序。</span><span class="sxs-lookup"><span data-stu-id="c548b-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="c548b-127">因此，`useModuleLevelNum`模組層級變數的值設定為 1。</span><span class="sxs-lookup"><span data-stu-id="c548b-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>  
  
     <span data-ttu-id="c548b-128">`MsgBox`呼叫內`show`略過所限定的遮蔽的機制`num`的模組名稱。</span><span class="sxs-lookup"><span data-stu-id="c548b-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="c548b-129">因此，它會顯示模組層級變數，而不是本機變數。</span><span class="sxs-lookup"><span data-stu-id="c548b-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="c548b-130">若要隱藏的變數，來透過繼承遮蔽</span><span class="sxs-lookup"><span data-stu-id="c548b-130">To hide a variable by shadowing it through inheritance</span></span>  
  
1.  <span data-ttu-id="c548b-131">請務必在您想要隱藏的變數宣告在類別中，並在類別層級 （以外的任何程序）。</span><span class="sxs-lookup"><span data-stu-id="c548b-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="c548b-132">否則您無法透過繼承遮蔽它。</span><span class="sxs-lookup"><span data-stu-id="c548b-132">Otherwise you cannot shadow it through inheritance.</span></span>  
  
2.  <span data-ttu-id="c548b-133">定義衍生自變數的類別，如果不存在的類別。</span><span class="sxs-lookup"><span data-stu-id="c548b-133">Define a class derived from the variable's class if one does not already exist.</span></span>  
  
3.  <span data-ttu-id="c548b-134">在衍生類別中，撰寫`Dim`陳述式來宣告變數。</span><span class="sxs-lookup"><span data-stu-id="c548b-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="c548b-135">包含[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c548b-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="c548b-136">當在衍生類別中的程式碼會參考變數的名稱時，編譯器會解析您變數的參考。</span><span class="sxs-lookup"><span data-stu-id="c548b-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="c548b-137">下列範例示範如何透過繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="c548b-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c548b-138">它可讓兩個參考，其中一個存取遮蔽的變數，略過遮蔽的其中一個。</span><span class="sxs-lookup"><span data-stu-id="c548b-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="c548b-139">上述範例中宣告變數`shadowString`基底類別中與遮蔽的衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="c548b-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c548b-140">此程序`showStrings`衍生類別中會顯示字串的遮蔽版本時名稱`shadowString`是非限定的。</span><span class="sxs-lookup"><span data-stu-id="c548b-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c548b-141">然後它會顯示的遮蔽的版本時`shadowString`是以限定`MyBase`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c548b-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c548b-142">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c548b-142">Robust Programming</span></span>  
 <span data-ttu-id="c548b-143">遮蔽導入了一個以上的版本，具有相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="c548b-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c548b-144">當程式碼陳述式參考的變數名稱時，編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定的字串存在。</span><span class="sxs-lookup"><span data-stu-id="c548b-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c548b-145">這樣可以增加參考到非預期的版本的受遮蔽變數的風險。</span><span class="sxs-lookup"><span data-stu-id="c548b-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="c548b-146">您可以降低風險，來完整限定遮蔽變數的所有參考。</span><span class="sxs-lookup"><span data-stu-id="c548b-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c548b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c548b-147">See also</span></span>

- [<span data-ttu-id="c548b-148">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="c548b-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c548b-149">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="c548b-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="c548b-150">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="c548b-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="c548b-151">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="c548b-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="c548b-152">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="c548b-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="c548b-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="c548b-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="c548b-154">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="c548b-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="c548b-155">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="c548b-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
