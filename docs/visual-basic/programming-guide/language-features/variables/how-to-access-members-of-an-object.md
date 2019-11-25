---
title: 如何：存取物件的成員
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348663"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="97f6b-102">如何：存取物件的成員 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97f6b-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="97f6b-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span><span class="sxs-lookup"><span data-stu-id="97f6b-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="97f6b-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span><span class="sxs-lookup"><span data-stu-id="97f6b-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="97f6b-105">Accessing Members</span><span class="sxs-lookup"><span data-stu-id="97f6b-105">Accessing Members</span></span>

<span data-ttu-id="97f6b-106">You access an object's members through the variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="97f6b-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="97f6b-107">To access members of an object</span><span class="sxs-lookup"><span data-stu-id="97f6b-107">To access members of an object</span></span>

- <span data-ttu-id="97f6b-108">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="97f6b-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="97f6b-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span><span class="sxs-lookup"><span data-stu-id="97f6b-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="97f6b-110">Accessing Members of an Object of Known Type</span><span class="sxs-lookup"><span data-stu-id="97f6b-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="97f6b-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="97f6b-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="97f6b-112">To access members of an object for which you know the type at compile time</span><span class="sxs-lookup"><span data-stu-id="97f6b-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="97f6b-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span><span class="sxs-lookup"><span data-stu-id="97f6b-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="97f6b-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="97f6b-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="97f6b-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span><span class="sxs-lookup"><span data-stu-id="97f6b-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="97f6b-116">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="97f6b-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="97f6b-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span><span class="sxs-lookup"><span data-stu-id="97f6b-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="97f6b-118">Accessing Members of an Object of Unknown Type</span><span class="sxs-lookup"><span data-stu-id="97f6b-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="97f6b-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span><span class="sxs-lookup"><span data-stu-id="97f6b-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="97f6b-120">To access members of an object for which you do not know the type at compile time</span><span class="sxs-lookup"><span data-stu-id="97f6b-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="97f6b-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="97f6b-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="97f6b-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="97f6b-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="97f6b-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span><span class="sxs-lookup"><span data-stu-id="97f6b-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="97f6b-124">Use the member-access operator (`.`) between the object variable name and the member name.</span><span class="sxs-lookup"><span data-stu-id="97f6b-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="97f6b-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="97f6b-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="97f6b-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span><span class="sxs-lookup"><span data-stu-id="97f6b-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="97f6b-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span><span class="sxs-lookup"><span data-stu-id="97f6b-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="97f6b-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="97f6b-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="97f6b-129">物件變數</span><span class="sxs-lookup"><span data-stu-id="97f6b-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="97f6b-130">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="97f6b-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="97f6b-131">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="97f6b-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="97f6b-132">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="97f6b-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
