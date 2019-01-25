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
ms.openlocfilehash: a2c476280009a617573fb7989b2184cd9baa6a8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660680"
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="ac564-102">物件變數指派 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac564-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="ac564-103">您可以使用一般的指派陳述式來將物件指派給物件變數。</span><span class="sxs-lookup"><span data-stu-id="ac564-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="ac564-104">您可以指派物件運算式或[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，如下列範例說明。</span><span class="sxs-lookup"><span data-stu-id="ac564-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="ac564-105">`Nothing` 表示沒有目前指派給變數的物件。</span><span class="sxs-lookup"><span data-stu-id="ac564-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="ac564-106">初始化</span><span class="sxs-lookup"><span data-stu-id="ac564-106">Initialization</span></span>  
 <span data-ttu-id="ac564-107">當您的程式碼開始執行，您的物件變數會初始化為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="ac564-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="ac564-108">其宣告包含初始化這些都會重新初始化，為您指定的宣告陳述式執行時的值。</span><span class="sxs-lookup"><span data-stu-id="ac564-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="ac564-109">您也可以使用在宣告中包含初始化[新增](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ac564-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="ac564-110">下列宣告陳述式宣告物件變數`testUri`和`ver`並為其指派特定的物件。</span><span class="sxs-lookup"><span data-stu-id="ac564-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="ac564-111">每個使用其中一個適當的類別的多載建構函式來初始化物件。</span><span class="sxs-lookup"><span data-stu-id="ac564-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("https://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="ac564-112">取消關聯</span><span class="sxs-lookup"><span data-stu-id="ac564-112">Disassociation</span></span>  
 <span data-ttu-id="ac564-113">若要設定物件變數`Nothing`中止的執行中的變數與任何特定物件的關聯。</span><span class="sxs-lookup"><span data-stu-id="ac564-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="ac564-114">這會防止您不小心變更藉由變更變數的物件。</span><span class="sxs-lookup"><span data-stu-id="ac564-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="ac564-115">它也可讓您測試物件變數是否指向有效的物件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ac564-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="ac564-116">如果您的變數所參考的物件是在另一個應用程式中，這項測試無法判斷該應用程式是否已結束，或是只失效的物件。</span><span class="sxs-lookup"><span data-stu-id="ac564-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="ac564-117">物件變數的值`Nothing`也稱為*為 null 參考*。</span><span class="sxs-lookup"><span data-stu-id="ac564-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="ac564-118">目前的執行個體</span><span class="sxs-lookup"><span data-stu-id="ac564-118">Current Instance</span></span>  
 <span data-ttu-id="ac564-119">*目前的執行個體*的物件是目前執行所在的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ac564-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="ac564-120">因為所有的程式碼會執行程序內，目前的執行個體是在其中叫用程序。</span><span class="sxs-lookup"><span data-stu-id="ac564-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="ac564-121">`Me`關鍵字做為物件變數參考目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ac564-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="ac564-122">如果不是程序[Shared](../../../../visual-basic/language-reference/modifiers/shared.md)，它可以使用`Me`關鍵字來取得目前的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="ac564-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="ac564-123">共用的程序不能與類別的特定執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="ac564-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="ac564-124">使用`Me`特別適用於將目前的執行個體傳遞至另一個模組中的程序。</span><span class="sxs-lookup"><span data-stu-id="ac564-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="ac564-125">例如，假設您有幾個 XML 文件，而且想要它們全部加入一些標準的文字。</span><span class="sxs-lookup"><span data-stu-id="ac564-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="ac564-126">下列範例會定義要執行這項操作的程序。</span><span class="sxs-lookup"><span data-stu-id="ac564-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="ac564-127">每個 XML 文件物件然後可以呼叫程序，並將其目前的執行個體傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="ac564-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="ac564-128">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="ac564-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac564-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac564-129">See also</span></span>
- [<span data-ttu-id="ac564-130">物件變數</span><span class="sxs-lookup"><span data-stu-id="ac564-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ac564-131">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="ac564-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="ac564-132">物件變數值</span><span class="sxs-lookup"><span data-stu-id="ac564-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="ac564-133">如何：宣告物件變數，並在 Visual Basic 中將物件指派給它</span><span class="sxs-lookup"><span data-stu-id="ac564-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [<span data-ttu-id="ac564-134">如何：讓物件變數不參考任何執行個體</span><span class="sxs-lookup"><span data-stu-id="ac564-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)
- [<span data-ttu-id="ac564-135">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="ac564-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
