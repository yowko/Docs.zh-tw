---
title: 如何：存取衍生類別所隱藏的變數
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345398"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="93ea4-102">如何：存取衍生類別所隱藏的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93ea4-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="93ea4-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span><span class="sxs-lookup"><span data-stu-id="93ea4-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="93ea4-104">If the variable is defined in the derived class, the code normally accesses that definition.</span><span class="sxs-lookup"><span data-stu-id="93ea4-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="93ea4-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span><span class="sxs-lookup"><span data-stu-id="93ea4-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="93ea4-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span><span class="sxs-lookup"><span data-stu-id="93ea4-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="93ea4-107">To access a base class variable hidden by a derived class</span><span class="sxs-lookup"><span data-stu-id="93ea4-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="93ea4-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span><span class="sxs-lookup"><span data-stu-id="93ea4-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="93ea4-109">The compiler resolves the reference to the base class version of the variable.</span><span class="sxs-lookup"><span data-stu-id="93ea4-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="93ea4-110">The following example illustrates shadowing through inheritance.</span><span class="sxs-lookup"><span data-stu-id="93ea4-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="93ea4-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span><span class="sxs-lookup"><span data-stu-id="93ea4-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="93ea4-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span><span class="sxs-lookup"><span data-stu-id="93ea4-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="93ea4-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span><span class="sxs-lookup"><span data-stu-id="93ea4-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="93ea4-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span><span class="sxs-lookup"><span data-stu-id="93ea4-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="93ea4-115">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="93ea4-115">Robust Programming</span></span>

<span data-ttu-id="93ea4-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="93ea4-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="93ea4-117">Shadowing introduces more than one version of a variable with the same name.</span><span class="sxs-lookup"><span data-stu-id="93ea4-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="93ea4-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span><span class="sxs-lookup"><span data-stu-id="93ea4-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="93ea4-119">This can increase the risk of referring to the wrong version of the variable.</span><span class="sxs-lookup"><span data-stu-id="93ea4-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="93ea4-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="93ea4-120">See also</span></span>

- [<span data-ttu-id="93ea4-121">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="93ea4-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="93ea4-122">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93ea4-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="93ea4-123">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="93ea4-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="93ea4-124">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="93ea4-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="93ea4-125">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="93ea4-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="93ea4-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="93ea4-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="93ea4-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="93ea4-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="93ea4-128">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="93ea4-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="93ea4-129">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="93ea4-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
