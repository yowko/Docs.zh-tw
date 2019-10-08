---
title: HOW TO：隱藏繼承的變數（Visual Basic）
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
ms.openlocfilehash: f575830df44076f694c1dfb2f68379594240fb80
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004840"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a><span data-ttu-id="16424-102">HOW TO：隱藏繼承的變數（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="16424-102">How to: Hide an Inherited Variable (Visual Basic)</span></span>

<span data-ttu-id="16424-103">衍生類別會繼承其基類的所有定義。</span><span class="sxs-lookup"><span data-stu-id="16424-103">A derived class inherits all the definitions of its base class.</span></span> <span data-ttu-id="16424-104">如果您想要使用與基類之專案相同的名稱來定義變數，您可以在衍生類別中定義變數時，隱藏或*遮蔽*該基類元素。</span><span class="sxs-lookup"><span data-stu-id="16424-104">If you want to define a variable using the same name as an element of the base class, you can hide, or *shadow*, that base class element when you define your variable in the derived class.</span></span> <span data-ttu-id="16424-105">如果您這樣做，衍生類別中的程式碼會存取您的變數，除非它明確略過遮蔽機制。</span><span class="sxs-lookup"><span data-stu-id="16424-105">If you do this, code in the derived class accesses your variable unless it explicitly bypasses the shadowing mechanism.</span></span>

<span data-ttu-id="16424-106">您可能會想要隱藏繼承的變數的另一個原因是要防止基底類別修訂。</span><span class="sxs-lookup"><span data-stu-id="16424-106">Another reason you might want to hide an inherited variable is to protect against base class revision.</span></span> <span data-ttu-id="16424-107">基類可能會改變您所繼承的元素。</span><span class="sxs-lookup"><span data-stu-id="16424-107">The base class might undergo a change that alters the element you are inheriting.</span></span> <span data-ttu-id="16424-108">如果發生這種情況，`Shadows` 修飾詞會強制將衍生類別的參考解析為您的變數，而不是基類元素。</span><span class="sxs-lookup"><span data-stu-id="16424-108">If this happens, the `Shadows` modifier forces references from the derived class to be resolved to your variable, instead of to the base class element.</span></span>

## <a name="to-hide-an-inherited-variable"></a><span data-ttu-id="16424-109">若要隱藏繼承的變數</span><span class="sxs-lookup"><span data-stu-id="16424-109">To hide an inherited variable</span></span>

1. <span data-ttu-id="16424-110">請確定您要隱藏的變數是在類別層級宣告（在任何程式之外）。</span><span class="sxs-lookup"><span data-stu-id="16424-110">Be sure the variable you want to hide is declared at class level (outside any procedure).</span></span> <span data-ttu-id="16424-111">否則，您不需要將它隱藏。</span><span class="sxs-lookup"><span data-stu-id="16424-111">Otherwise, you do not need to hide it.</span></span>
  
2. <span data-ttu-id="16424-112">在您的衍生類別中，撰寫宣告變數的[Dim 語句](../../../language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="16424-112">Inside your derived class, write a [Dim Statement](../../../language-reference/statements/dim-statement.md) declaring your variable.</span></span> <span data-ttu-id="16424-113">使用與繼承之變數相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="16424-113">Use the same name as that of the inherited variable.</span></span>

3. <span data-ttu-id="16424-114">在宣告中包含[Shadows](../../../language-reference/modifiers/shadows.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="16424-114">Include the [Shadows](../../../language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

     <span data-ttu-id="16424-115">當衍生類別中的程式碼參考變數名稱時，編譯器會解析變數的參考。</span><span class="sxs-lookup"><span data-stu-id="16424-115">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

     <span data-ttu-id="16424-116">下列範例說明如何遮蔽繼承的變數：</span><span class="sxs-lookup"><span data-stu-id="16424-116">The following example illustrates shadowing of an inherited variable:</span></span>
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     <span data-ttu-id="16424-117">上述範例會在基類中宣告變數 `shadowString`，並將其遮蔽在衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="16424-117">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="16424-118">當名稱 `shadowString` 不合格時，衍生類別中 `ShowStrings` 的程式會顯示字串的遮蔽版本。</span><span class="sxs-lookup"><span data-stu-id="16424-118">The procedure `ShowStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="16424-119">然後，它會在使用 `MyBase` 關鍵字限定 `shadowString` 時，顯示陰影的版本。</span><span class="sxs-lookup"><span data-stu-id="16424-119">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="16424-120">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="16424-120">Robust programming</span></span>

<span data-ttu-id="16424-121">遮蔽導入了一個以上具有相同名稱的變數版本。</span><span class="sxs-lookup"><span data-stu-id="16424-121">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="16424-122">當程式碼語句參考變數名稱時，編譯器解析參考的目標版本取決於程式碼語句的位置，以及符合資格的字串是否存在等因素。</span><span class="sxs-lookup"><span data-stu-id="16424-122">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="16424-123">這可能會增加參考非預期版本的陰影變數的風險。</span><span class="sxs-lookup"><span data-stu-id="16424-123">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="16424-124">您可以藉由完整限定遮蔽變數的所有參考，來降低風險。</span><span class="sxs-lookup"><span data-stu-id="16424-124">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="16424-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16424-125">See also</span></span>

- [<span data-ttu-id="16424-126">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="16424-126">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="16424-127">Visual Basic 中的陰影</span><span class="sxs-lookup"><span data-stu-id="16424-127">Shadowing in Visual Basic</span></span>](shadowing.md)
- [<span data-ttu-id="16424-128">遮蔽和覆寫的差異</span><span class="sxs-lookup"><span data-stu-id="16424-128">Differences Between Shadowing and Overriding</span></span>](differences-between-shadowing-and-overriding.md)
- <span data-ttu-id="16424-129">[如何：隱藏與您的變數名稱相同的變數 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="16424-129">[How to: Hide a Variable with the Same Name as Your Variable](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)</span></span>
- <span data-ttu-id="16424-130">[如何：存取衍生類別所隱藏的變數 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="16424-130">[How to: Access a Variable Hidden by a Derived Class](how-to-access-a-variable-hidden-by-a-derived-class.md)</span></span>
- [<span data-ttu-id="16424-131">Overrides</span><span class="sxs-lookup"><span data-stu-id="16424-131">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="16424-132">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="16424-132">Me, My, MyBase, and MyClass</span></span>](../../program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="16424-133">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="16424-133">Inheritance Basics</span></span>](../objects-and-classes/inheritance-basics.md)
