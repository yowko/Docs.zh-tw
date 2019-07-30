---
title: 作法：存取衍生類別所隱藏的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 68f92142cdc435ebd82101eea83035e1d09dcf25
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630011"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="68076-102">HOW TO：存取衍生類別所隱藏的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68076-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>

<span data-ttu-id="68076-103">當衍生類別中的程式碼存取變數時, 編譯器通常會將參考解析成最接近的可存取版本, 也就是可存取的版本, 最少的 derivational 步驟是從存取類別回溯。</span><span class="sxs-lookup"><span data-stu-id="68076-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="68076-104">如果變數是在衍生類別中定義, 則程式碼通常會存取該定義。</span><span class="sxs-lookup"><span data-stu-id="68076-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>

<span data-ttu-id="68076-105">如果衍生類別變數遮蔽基類中的變數, 則會隱藏基類版本。</span><span class="sxs-lookup"><span data-stu-id="68076-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="68076-106">不過, 您可以使用`MyBase`關鍵字來限定基類變數來存取它。</span><span class="sxs-lookup"><span data-stu-id="68076-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="68076-107">存取衍生類別所隱藏的基類變數</span><span class="sxs-lookup"><span data-stu-id="68076-107">To access a base class variable hidden by a derived class</span></span>

- <span data-ttu-id="68076-108">在運算式或指派語句中, 在變數名稱`MyBase`前面加上關鍵字和句點 (`.`)。</span><span class="sxs-lookup"><span data-stu-id="68076-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>

    <span data-ttu-id="68076-109">編譯器會解析變數的基底類別版本參考。</span><span class="sxs-lookup"><span data-stu-id="68076-109">The compiler resolves the reference to the base class version of the variable.</span></span>

    <span data-ttu-id="68076-110">下列範例說明透過繼承的遮蔽。</span><span class="sxs-lookup"><span data-stu-id="68076-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="68076-111">它會建立兩個參考, 一個存取遮蔽變數, 另一個則會略過遮蔽。</span><span class="sxs-lookup"><span data-stu-id="68076-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

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

    <span data-ttu-id="68076-112">上述範例會在基類中`shadowString`宣告變數, 並將其遮蔽在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="68076-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="68076-113">當名稱`shadowString`未限定時, 衍生類別中的程式會顯示字串的遮蔽版本。`showStrings`</span><span class="sxs-lookup"><span data-stu-id="68076-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="68076-114">然後, 它會在`shadowString` `MyBase`以關鍵字限定時顯示陰影版本。</span><span class="sxs-lookup"><span data-stu-id="68076-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="68076-115">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="68076-115">Robust Programming</span></span>

<span data-ttu-id="68076-116">若要降低參照非預期版本的陰影變數的風險, 您可以完整限定遮蔽變數的所有參考。</span><span class="sxs-lookup"><span data-stu-id="68076-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="68076-117">遮蔽導入了一個以上具有相同名稱的變數版本。</span><span class="sxs-lookup"><span data-stu-id="68076-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="68076-118">當程式碼語句參考變數名稱時, 編譯器解析參考的目標版本取決於程式碼語句的位置, 以及符合資格的字串是否存在等因素。</span><span class="sxs-lookup"><span data-stu-id="68076-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="68076-119">這可能會增加參考錯誤版本的變數的風險。</span><span class="sxs-lookup"><span data-stu-id="68076-119">This can increase the risk of referring to the wrong version of the variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="68076-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68076-120">See also</span></span>

- [<span data-ttu-id="68076-121">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="68076-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="68076-122">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="68076-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="68076-123">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="68076-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="68076-124">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="68076-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="68076-125">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="68076-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="68076-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="68076-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="68076-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="68076-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="68076-128">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="68076-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="68076-129">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="68076-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
