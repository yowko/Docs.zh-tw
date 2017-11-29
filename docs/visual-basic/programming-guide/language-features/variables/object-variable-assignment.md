---
title: "物件變數指派 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb6b53bebddc1c9cf1b9088e96ded36a5e1c5242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="object-variable-assignment-visual-basic"></a><span data-ttu-id="4e53a-102">物件變數指派 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e53a-102">Object Variable Assignment (Visual Basic)</span></span>
<span data-ttu-id="4e53a-103">您可以使用一般的指派陳述式來指派給物件變數的物件。</span><span class="sxs-lookup"><span data-stu-id="4e53a-103">You use a normal assignment statement to assign an object to an object variable.</span></span> <span data-ttu-id="4e53a-104">您可以指派物件運算式或[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，如下列範例說明。</span><span class="sxs-lookup"><span data-stu-id="4e53a-104">You can assign an object expression or the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, as the following example illustrates.</span></span>  
  
```  
Dim thisObject As Object  
' The following statement assigns an object reference.  
thisObject = Form1  
' The following statement discontinues association with any object.  
thisObject = Nothing  
```  
  
 <span data-ttu-id="4e53a-105">`Nothing`表示沒有目前指派給變數的物件。</span><span class="sxs-lookup"><span data-stu-id="4e53a-105">`Nothing` means there is no object currently assigned to the variable.</span></span>  
  
## <a name="initialization"></a><span data-ttu-id="4e53a-106">初始化</span><span class="sxs-lookup"><span data-stu-id="4e53a-106">Initialization</span></span>  
 <span data-ttu-id="4e53a-107">當您的程式碼開始執行，您的物件變數初始化為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="4e53a-107">When your code begins running, your object variables are initialized to `Nothing`.</span></span> <span data-ttu-id="4e53a-108">重新初始化其宣告包含初始化這些宣告陳述式執行時，您指定的值。</span><span class="sxs-lookup"><span data-stu-id="4e53a-108">Those whose declarations include initialization are reinitialized to the values you specify when the declaration statements are executed.</span></span>  
  
 <span data-ttu-id="4e53a-109">您也可以使用在宣告中包含初始化[新增](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="4e53a-109">You can include initialization in your declaration by using the [New](../../../../visual-basic/language-reference/operators/new-operator.md) keyword.</span></span> <span data-ttu-id="4e53a-110">下列宣告陳述式宣告物件變數`testUri`和`ver`並為其指派的特定物件。</span><span class="sxs-lookup"><span data-stu-id="4e53a-110">The following declaration statements declare object variables `testUri` and `ver` and assign specific objects to them.</span></span> <span data-ttu-id="4e53a-111">使用其中一個適當的類別的多載建構函式以初始化物件。</span><span class="sxs-lookup"><span data-stu-id="4e53a-111">Each uses one of the overloaded constructors of the appropriate class to initialize the object.</span></span>  
  
```  
Dim testUri As New System.Uri("http://www.microsoft.com")  
Dim ver As New System.Version(6, 1, 0)  
```  
  
## <a name="disassociation"></a><span data-ttu-id="4e53a-112">取消關聯</span><span class="sxs-lookup"><span data-stu-id="4e53a-112">Disassociation</span></span>  
 <span data-ttu-id="4e53a-113">若要設定物件變數`Nothing`停止與任何特定物件的變數關聯。</span><span class="sxs-lookup"><span data-stu-id="4e53a-113">Setting an object variable to `Nothing` discontinues the association of the variable with any specific object.</span></span> <span data-ttu-id="4e53a-114">這可防止不小心變更物件變更的變數。</span><span class="sxs-lookup"><span data-stu-id="4e53a-114">This prevents you from accidentally changing the object by changing the variable.</span></span> <span data-ttu-id="4e53a-115">它也可讓您測試物件變數是否指向有效的物件，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4e53a-115">It also allows you to test whether the object variable points to a valid object, as the following example shows.</span></span>  
  
```  
If otherObject IsNot Nothing Then  
    ' otherObject refers to a valid object, so your code can use it.  
End If  
```  
  
 <span data-ttu-id="4e53a-116">如果您的變數所參考的物件位於另一個應用程式，這項測試無法判斷該應用程式是否已結束，或是只失效的物件。</span><span class="sxs-lookup"><span data-stu-id="4e53a-116">If the object your variable refers to is in another application, this test cannot determine whether that application has terminated or just invalidated the object.</span></span>  
  
 <span data-ttu-id="4e53a-117">物件變數值是`Nothing`也稱為*null 參考*。</span><span class="sxs-lookup"><span data-stu-id="4e53a-117">An object variable with a value of `Nothing` is also called a *null reference*.</span></span>  
  
## <a name="current-instance"></a><span data-ttu-id="4e53a-118">目前執行個體</span><span class="sxs-lookup"><span data-stu-id="4e53a-118">Current Instance</span></span>  
 <span data-ttu-id="4e53a-119">*目前執行個體*的物件是在其中目前執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="4e53a-119">The *current instance* of an object is the one in which the code is currently executing.</span></span> <span data-ttu-id="4e53a-120">由於所有的程式碼會執行程序內，目前的執行個體是程序已叫用。</span><span class="sxs-lookup"><span data-stu-id="4e53a-120">Since all code executes inside a procedure, the current instance is the one in which the procedure was invoked.</span></span>  
  
 <span data-ttu-id="4e53a-121">`Me`關鍵字做為物件變數參考目前的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4e53a-121">The `Me` keyword acts as an object variable referring to the current instance.</span></span> <span data-ttu-id="4e53a-122">如果不是程序[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，它可以使用`Me`關鍵字來取得目前的執行個體的指標。</span><span class="sxs-lookup"><span data-stu-id="4e53a-122">If a procedure is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), it can use the `Me` keyword to obtain a pointer to the current instance.</span></span> <span data-ttu-id="4e53a-123">共用的程序不能與類別的特定執行個體相關聯。</span><span class="sxs-lookup"><span data-stu-id="4e53a-123">Shared procedures cannot be associated with a specific instance of a class.</span></span>  
  
 <span data-ttu-id="4e53a-124">使用`Me`將目前的執行個體傳遞至另一個模組中的程序特別有用。</span><span class="sxs-lookup"><span data-stu-id="4e53a-124">Using `Me` is particularly useful for passing the current instance to a procedure in another module.</span></span> <span data-ttu-id="4e53a-125">例如，假設您的 XML 文件數目與要加入至所有端點的一些標準的文字。</span><span class="sxs-lookup"><span data-stu-id="4e53a-125">For example, suppose you have a number of XML documents and wish to add some standard text to all of them.</span></span> <span data-ttu-id="4e53a-126">下列範例會定義可執行此動作的程序。</span><span class="sxs-lookup"><span data-stu-id="4e53a-126">The following example defines a procedure to do this.</span></span>  
  
```  
Sub addStandardText(XmlDoc As System.Xml.XmlDocument)  
    XmlDoc.CreateTextNode("This text goes into every XML document.")  
End Sub  
```  
  
 <span data-ttu-id="4e53a-127">每個 XML 文件物件無法呼叫程序，然後將其目前的執行個體傳遞做為引數。</span><span class="sxs-lookup"><span data-stu-id="4e53a-127">Every XML document object could then call the procedure and pass its current instance as an argument.</span></span> <span data-ttu-id="4e53a-128">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="4e53a-128">The following example demonstrates this.</span></span>  
  
```  
addStandardText(Me)  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e53a-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e53a-129">See Also</span></span>  
 [<span data-ttu-id="4e53a-130">物件變數</span><span class="sxs-lookup"><span data-stu-id="4e53a-130">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="4e53a-131">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="4e53a-131">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="4e53a-132">物件變數值</span><span class="sxs-lookup"><span data-stu-id="4e53a-132">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="4e53a-133">如何： 宣告物件變數，並在 Visual Basic 中為其指派物件</span><span class="sxs-lookup"><span data-stu-id="4e53a-133">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [<span data-ttu-id="4e53a-134">如何：讓物件變數不參考執行個體</span><span class="sxs-lookup"><span data-stu-id="4e53a-134">How to: Make an Object Variable Not Refer to Any Instance</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-make-an-object-variable-not-refer-to-any-instance.md)  
 [<span data-ttu-id="4e53a-135">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="4e53a-135">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
