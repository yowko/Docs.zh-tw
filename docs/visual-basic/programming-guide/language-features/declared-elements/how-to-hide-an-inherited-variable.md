---
title: HOW TO：隱藏繼承的變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: 6cf45b12bebc254a0d96516ab262d7aae3d70746
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691251"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="9fe55-102">HOW TO：隱藏繼承的變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fe55-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>
<span data-ttu-id="9fe55-103">在衍生的類別會繼承其基底類別的所有定義。</span><span class="sxs-lookup"><span data-stu-id="9fe55-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="9fe55-104">如果您想要定義為基底類別的項目使用相同名稱的變數，您可以將它隱藏，或*陰影*，當您在衍生類別中定義您的變數時，該基底類別項目。</span><span class="sxs-lookup"><span data-stu-id="9fe55-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="9fe55-105">如果您這麼做時，衍生類別中的程式碼會存取您的變數，除非它明確會略過的遮蔽的機制。</span><span class="sxs-lookup"><span data-stu-id="9fe55-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>  
  
 <span data-ttu-id="9fe55-106">您可能想要隱藏繼承的變數的另一個原因是要保護修訂基底類別。</span><span class="sxs-lookup"><span data-stu-id="9fe55-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="9fe55-107">基底類別可能進行的變更會改變您繼承的項目。</span><span class="sxs-lookup"><span data-stu-id="9fe55-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="9fe55-108">如果發生這種情況，`Shadows`修飾詞會強制從衍生的類別，為您的變數，而不是解析至基底類別項目參考。</span><span class="sxs-lookup"><span data-stu-id="9fe55-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>  
  
### <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="9fe55-109">若要隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="9fe55-109">To hide an inherited variable</span></span>  
  
1.  <span data-ttu-id="9fe55-110">請務必在您想要隱藏的變數宣告類別層級 （以外的任何程序）。</span><span class="sxs-lookup"><span data-stu-id="9fe55-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="9fe55-111">否則您不需要加以隱藏。</span><span class="sxs-lookup"><span data-stu-id="9fe55-111">Otherwise you do not need to hide it.</span></span>  
  
2.  <span data-ttu-id="9fe55-112">在衍生類別中，撰寫[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)宣告您的變數。</span><span class="sxs-lookup"><span data-stu-id="9fe55-112">Inside your derived class, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="9fe55-113">使用相同名稱的繼承的變數。</span><span class="sxs-lookup"><span data-stu-id="9fe55-113">Use the same name as that of the inherited variable.</span></span>  
  
3.  <span data-ttu-id="9fe55-114">包含[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)宣告中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9fe55-114">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>  
  
     <span data-ttu-id="9fe55-115">當在衍生類別中的程式碼會參考變數的名稱時，編譯器會解析您變數的參考。</span><span class="sxs-lookup"><span data-stu-id="9fe55-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>  
  
     <span data-ttu-id="9fe55-116">下列範例示範如何遮蔽的繼承的變數。</span><span class="sxs-lookup"><span data-stu-id="9fe55-116">The following example illustrates shadowing of an inherited variable.</span></span>  
  
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
  
     <span data-ttu-id="9fe55-117">上述範例中宣告變數`shadowString`基底類別中與遮蔽的衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="9fe55-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="9fe55-118">此程序`showStrings`衍生類別中會顯示字串的遮蔽版本時名稱`shadowString`是非限定的。</span><span class="sxs-lookup"><span data-stu-id="9fe55-118">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="9fe55-119">然後它會顯示的遮蔽的版本時`shadowString`是以限定`MyBase`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="9fe55-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9fe55-120">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="9fe55-120">Robust Programming</span></span>  
 <span data-ttu-id="9fe55-121">遮蔽導入了一個以上的版本，具有相同名稱的變數。</span><span class="sxs-lookup"><span data-stu-id="9fe55-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="9fe55-122">當程式碼陳述式參考的變數名稱時，編譯器會解析參考的版本取決於因素，例如程式碼陳述式的位置和限定的字串存在。</span><span class="sxs-lookup"><span data-stu-id="9fe55-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="9fe55-123">這樣可以增加參考到非預期的版本的受遮蔽變數的風險。</span><span class="sxs-lookup"><span data-stu-id="9fe55-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="9fe55-124">您可以降低風險，來完整限定遮蔽變數的所有參考。</span><span class="sxs-lookup"><span data-stu-id="9fe55-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe55-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9fe55-125">See also</span></span>
- [<span data-ttu-id="9fe55-126">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="9fe55-126">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="9fe55-127">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="9fe55-127">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="9fe55-128">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="9fe55-128">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="9fe55-129">如何：隱藏與您的變數名稱相同的變數</span><span class="sxs-lookup"><span data-stu-id="9fe55-129">How to: Hide a Variable with the Same Name as Your Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [<span data-ttu-id="9fe55-130">如何：存取衍生類別所隱藏的變數</span><span class="sxs-lookup"><span data-stu-id="9fe55-130">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="9fe55-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="9fe55-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="9fe55-132">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="9fe55-132">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="9fe55-133">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="9fe55-133">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
