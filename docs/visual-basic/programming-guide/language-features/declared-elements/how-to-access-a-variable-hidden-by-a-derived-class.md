---
title: HOW TO：存取衍生類別 (Visual Basic) 所隱藏的變數
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 43f7af1a1b540dd630cc2f228f1e5a6018d7c5d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610463"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a><span data-ttu-id="c63ff-102">HOW TO：存取衍生類別 (Visual Basic) 所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="c63ff-102">How to: Access a Variable Hidden by a Derived Class (Visual Basic)</span></span>
<span data-ttu-id="c63ff-103">當在衍生類別中的程式碼存取的變數時，編譯器通常會將參考解析最接近的可存取版本，也就是可存取的版本的最少衍生步驟回溯正在存取的類別。</span><span class="sxs-lookup"><span data-stu-id="c63ff-103">When code in a derived class accesses a variable, the compiler normally resolves the reference to the closest accessible version, that is, the accessible version the fewest derivational steps backward from the accessing class.</span></span> <span data-ttu-id="c63ff-104">如果變數定義在衍生類別中，程式碼通常會存取該定義。</span><span class="sxs-lookup"><span data-stu-id="c63ff-104">If the variable is defined in the derived class, the code normally accesses that definition.</span></span>  
  
 <span data-ttu-id="c63ff-105">如果在衍生的類別變數會遮蔽基底類別中的變數，則會隱藏基底類別版本。</span><span class="sxs-lookup"><span data-stu-id="c63ff-105">If the derived class variable shadows a variable in the base class, it hides the base class version.</span></span> <span data-ttu-id="c63ff-106">不過，您可以存取的基底類別變數限定它與`MyBase`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c63ff-106">However, you can access the base class variable by qualifying it with the `MyBase` keyword.</span></span>  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a><span data-ttu-id="c63ff-107">若要存取衍生類別所隱藏的基底類別變數</span><span class="sxs-lookup"><span data-stu-id="c63ff-107">To access a base class variable hidden by a derived class</span></span>  
  
- <span data-ttu-id="c63ff-108">在運算式或指派陳述式中，變數名稱前加`MyBase`關鍵字和句號 (`.`)。</span><span class="sxs-lookup"><span data-stu-id="c63ff-108">In an expression or assignment statement, precede the variable name with the `MyBase` keyword and a period (`.`).</span></span>  
  
     <span data-ttu-id="c63ff-109">編譯器會解析變數的基底類別版本的參考。</span><span class="sxs-lookup"><span data-stu-id="c63ff-109">The compiler resolves the reference to the base class version of the variable.</span></span>  
  
     <span data-ttu-id="c63ff-110">下列範例示範如何透過繼承遮蔽。</span><span class="sxs-lookup"><span data-stu-id="c63ff-110">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="c63ff-111">它可讓兩個參考，其中一個存取遮蔽的變數，略過遮蔽的其中一個。</span><span class="sxs-lookup"><span data-stu-id="c63ff-111">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>  
  
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
  
     <span data-ttu-id="c63ff-112">上述範例中宣告變數`shadowString`基底類別中與遮蔽的衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="c63ff-112">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="c63ff-113">此程序`showStrings`衍生類別中會顯示字串的遮蔽版本時名稱`shadowString`是非限定的。</span><span class="sxs-lookup"><span data-stu-id="c63ff-113">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="c63ff-114">然後它會顯示的遮蔽的版本時`shadowString`是以限定`MyBase`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c63ff-114">It then displays the shadowed version when `shadowString` is qualified with the `MyBase`  keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c63ff-115">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c63ff-115">Robust Programming</span></span>  
 <span data-ttu-id="c63ff-116">若要降低非預期的版本的受遮蔽變數所參考的風險，您可以完整限定遮蔽變數的所有參考。</span><span class="sxs-lookup"><span data-stu-id="c63ff-116">To lower the risk of referring to an unintended version of a shadowed variable, you can fully qualify all references to a shadowed variable.</span></span> <span data-ttu-id="c63ff-117">遮蔽導入了一個以上的版本，具有相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="c63ff-117">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="c63ff-118">當程式碼陳述式參考的變數名稱時，編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定的字串存在。</span><span class="sxs-lookup"><span data-stu-id="c63ff-118">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="c63ff-119">這樣可以增加參考變數的版本錯誤的風險。</span><span class="sxs-lookup"><span data-stu-id="c63ff-119">This can increase the risk of referring to the wrong version of the variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c63ff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c63ff-120">See also</span></span>

- [<span data-ttu-id="c63ff-121">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="c63ff-121">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c63ff-122">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="c63ff-122">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="c63ff-123">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="c63ff-123">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="c63ff-124">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="c63ff-124">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="c63ff-125">如何：隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="c63ff-125">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="c63ff-126">Shadows</span><span class="sxs-lookup"><span data-stu-id="c63ff-126">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="c63ff-127">Overrides</span><span class="sxs-lookup"><span data-stu-id="c63ff-127">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="c63ff-128">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="c63ff-128">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="c63ff-129">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="c63ff-129">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
