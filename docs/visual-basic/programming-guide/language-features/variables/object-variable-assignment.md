---
title: 物件變數指派 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], object variable assignment
- object variables [Visual Basic], initializing
- variables [Visual Basic], initializing
- objects [Visual Basic], current instance
- object variables [Visual Basic], assigning
- variables [Visual Basic], object variables
- current instance [Visual Basic], defined
- variables [Visual Basic], assigning
- assignment statements [Visual Basic], object variable assignment
- Me keyword [Visual Basic], as object variable
ms.assetid: 3706811d-fd40-44fe-8727-d692e8e55d6d
ms.openlocfilehash: 59dea45511ba8d7d10c95cf17e47981124c532e4
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631050"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="b580c-102">物件變數指派 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b580c-102">Object Variable Assignment (Visual Basic)</span></span>

<span data-ttu-id="b580c-103">您可以使用一般指派語句, 將物件指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="b580c-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="b580c-104">您可以指派物件運算式或不使用[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b580c-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>

```vb
Dim thisObject As Object
' The following statement assigns an object reference.
thisObject = Form1
' The following statement discontinues association with any object.
thisObject = Nothing
```

<span data-ttu-id="b580c-105">`Nothing`表示目前沒有任何物件指派給該變數。</span><span class="sxs-lookup"><span data-stu-id="b580c-105">`Nothing` means there is no object currently assigned to the variable.</span></span>

## <a name="initialization"></a><span data-ttu-id="b580c-106">初始化</span><span class="sxs-lookup"><span data-stu-id="b580c-106">Initialization</span></span>

<span data-ttu-id="b580c-107">當您的程式碼開始執行時, 您的物件`Nothing`變數會初始化為。</span><span class="sxs-lookup"><span data-stu-id="b580c-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="b580c-108">其宣告包含初始化的使用者會重新初始化為您在宣告語句執行時所指定的值。</span><span class="sxs-lookup"><span data-stu-id="b580c-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>

<span data-ttu-id="b580c-109">您可以使用[New](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字, 在宣告中包含初始化。</span><span class="sxs-lookup"><span data-stu-id="b580c-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="b580c-110">下列宣告語句會宣告物件變數`testUri` , `ver`並將特定物件指派給它們。</span><span class="sxs-lookup"><span data-stu-id="b580c-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="b580c-111">每個都會使用適當類別的其中一個多載的函式來初始化物件。</span><span class="sxs-lookup"><span data-stu-id="b580c-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>

```vb
Dim testUri As New System.Uri("https://www.microsoft.com")
Dim ver As New System.Version(6, 1, 0)
```

## <a name="disassociation"></a><span data-ttu-id="b580c-112">解除</span><span class="sxs-lookup"><span data-stu-id="b580c-112">Disassociation</span></span>

<span data-ttu-id="b580c-113">設定物件變數以`Nothing`中止變數與任何特定物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="b580c-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="b580c-114">這可防止您藉由變更變數而不小心變更物件。</span><span class="sxs-lookup"><span data-stu-id="b580c-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="b580c-115">它也可讓您測試物件變數是否指向有效的物件, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b580c-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>

```vb
If otherObject IsNot Nothing Then
    ' otherObject refers to a valid object, so your code can use it.
End If
```

<span data-ttu-id="b580c-116">如果您的變數所參考的物件位於另一個應用程式中, 則此測試無法判斷該應用程式是否已終止, 或只使物件失效。</span><span class="sxs-lookup"><span data-stu-id="b580c-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>

<span data-ttu-id="b580c-117">值為的`Nothing`物件變數也稱為*null 參考*。</span><span class="sxs-lookup"><span data-stu-id="b580c-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>

## <a name="current-instance"></a><span data-ttu-id="b580c-118">目前的實例</span><span class="sxs-lookup"><span data-stu-id="b580c-118">Current Instance</span></span>

<span data-ttu-id="b580c-119">目前物件的實例就是程式碼執行所在的*實例*。</span><span class="sxs-lookup"><span data-stu-id="b580c-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="b580c-120">由於所有程式碼都是在程式中執行, 因此目前的實例就是叫用此程式的其中一個。</span><span class="sxs-lookup"><span data-stu-id="b580c-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>

<span data-ttu-id="b580c-121">`Me`關鍵字會作為參考目前實例的物件變數。</span><span class="sxs-lookup"><span data-stu-id="b580c-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="b580c-122">如果程式不是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的, 它可以使用`Me`關鍵字來取得目前實例的指標。</span><span class="sxs-lookup"><span data-stu-id="b580c-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="b580c-123">共用程式無法與類別的特定實例建立關聯。</span><span class="sxs-lookup"><span data-stu-id="b580c-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>

<span data-ttu-id="b580c-124">使用`Me`特別適合用來將目前的實例傳遞至另一個模組中的程式。</span><span class="sxs-lookup"><span data-stu-id="b580c-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="b580c-125">例如, 假設您有多個 XML 檔, 而且想要在其中新增一些標準文字。</span><span class="sxs-lookup"><span data-stu-id="b580c-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="b580c-126">下列範例會定義執行這項操作的程式。</span><span class="sxs-lookup"><span data-stu-id="b580c-126">The following example defines a procedure to do this.</span></span>

```vb
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)
    XmlDoc.CreateTextNode("This text goes into every XML document.")
End Sub
```

<span data-ttu-id="b580c-127">然後, 每個 XML 檔物件都可以呼叫程式, 並將其目前的實例當做引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="b580c-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="b580c-128">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="b580c-128">The following example demonstrates this.</span></span>

```vb
addStandardText(Me)
```

## <a name="see-also"></a><span data-ttu-id="b580c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b580c-129">See also</span></span>

- [<span data-ttu-id="b580c-130">物件變數</span><span class="sxs-lookup"><span data-stu-id="b580c-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="b580c-131">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="b580c-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="b580c-132">物件變數值</span><span class="sxs-lookup"><span data-stu-id="b580c-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="b580c-133">如何：在 Visual Basic 中, 宣告物件變數並指派物件給它</span><span class="sxs-lookup"><span data-stu-id="b580c-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="b580c-134">如何：讓物件變數不參考任何實例</span><span class="sxs-lookup"><span data-stu-id="b580c-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="b580c-135">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b580c-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
