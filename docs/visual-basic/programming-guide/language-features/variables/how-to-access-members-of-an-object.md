---
title: "如何：存取物件的成員 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 85fa4932b449bf7b9ecb3902fc17fd954ea8cfac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="86626-102">如何：存取物件的成員 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86626-102">How to: Access Members of an Object (Visual Basic)</span></span>
<span data-ttu-id="86626-103">當您參考之物件的物件變數時，您通常會想要使用該物件，例如方法、 屬性、 欄位和事件的成員。</span><span class="sxs-lookup"><span data-stu-id="86626-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="86626-104">例如，一次您建立新<xref:System.Windows.Forms.Form>物件，您可能想要設定其<xref:System.Windows.Forms.Control.Text%2A>屬性或呼叫其<xref:System.Windows.Forms.Control.Focus%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="86626-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>  
  
## <a name="accessing-members"></a><span data-ttu-id="86626-105">存取成員</span><span class="sxs-lookup"><span data-stu-id="86626-105">Accessing Members</span></span>  
 <span data-ttu-id="86626-106">您可以存取物件的成員透過參考該變數。</span><span class="sxs-lookup"><span data-stu-id="86626-106">You access an object's members through the variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="86626-107">若要存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="86626-107">To access members of an object</span></span>  
  
-   <span data-ttu-id="86626-108">使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="86626-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     <span data-ttu-id="86626-109">如果成員是[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，您不需要存取的變數。</span><span class="sxs-lookup"><span data-stu-id="86626-109">If the member is [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>  
  
## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="86626-110">存取已知型別的物件的成員</span><span class="sxs-lookup"><span data-stu-id="86626-110">Accessing Members of an Object of Known Type</span></span>  
 <span data-ttu-id="86626-111">如果您在編譯時間知道物件類型，您可以使用*早期繫結*參考該變數。</span><span class="sxs-lookup"><span data-stu-id="86626-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="86626-112">若要存取，您必須知道類型在編譯時期物件的成員</span><span class="sxs-lookup"><span data-stu-id="86626-112">To access members of an object for which you know the type at compile time</span></span>  
  
1.  <span data-ttu-id="86626-113">宣告物件變數，是您想要指派給變數物件的類型。</span><span class="sxs-lookup"><span data-stu-id="86626-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     <span data-ttu-id="86626-114">與`Option Strict On`，您可以只指派<xref:System.Windows.Forms.Form>物件 (或類型的物件衍生自<xref:System.Windows.Forms.Form>) 至`extraForm`。</span><span class="sxs-lookup"><span data-stu-id="86626-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="86626-115">如果您已定義類別或結構與擴展`CType`轉換成<xref:System.Windows.Forms.Form>，您也可以指定該類別或結構以`extraForm`。</span><span class="sxs-lookup"><span data-stu-id="86626-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>  
  
2.  <span data-ttu-id="86626-116">使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="86626-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    extraForm.Show()  
    ```  
  
     <span data-ttu-id="86626-117">您可以存取的所有方法和屬性的特定<xref:System.Windows.Forms.Form>類別，無論什麼`Option Strict`設定。</span><span class="sxs-lookup"><span data-stu-id="86626-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="86626-118">存取成員的未知類型的物件</span><span class="sxs-lookup"><span data-stu-id="86626-118">Accessing Members of an Object of Unknown Type</span></span>  
 <span data-ttu-id="86626-119">如果您不知道物件類型在編譯時期，您必須使用*晚期繫結*指的是它的任何變數。</span><span class="sxs-lookup"><span data-stu-id="86626-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="86626-120">若要存取，您不知道類型在編譯時期物件的成員</span><span class="sxs-lookup"><span data-stu-id="86626-120">To access members of an object for which you do not know the type at compile time</span></span>  
  
1.  <span data-ttu-id="86626-121">宣告物件變數是[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="86626-121">Declare the object variable to be of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="86626-122">(變數宣告為`Object`等同於它宣告為<xref:System.Object?displayProperty=nameWithType>。)</span><span class="sxs-lookup"><span data-stu-id="86626-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>  
  
    ```  
    Dim someControl As Object  
    ```  
  
     <span data-ttu-id="86626-123">與`Option Strict On`，您可以存取上定義之成員<xref:System.Object>類別。</span><span class="sxs-lookup"><span data-stu-id="86626-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>  
  
2.  <span data-ttu-id="86626-124">使用成員存取運算子 (`.`) 之間的物件變數的名稱和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="86626-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>  
  
    ```  
    someControl.GetType()  
    ```  
  
     <span data-ttu-id="86626-125">若要能夠存取您指派給物件變數的任何物件的成員，您必須設定`Option Strict Off`。</span><span class="sxs-lookup"><span data-stu-id="86626-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="86626-126">當您這樣做時，編譯器無法保證指定的成員由您指派給變數的物件。</span><span class="sxs-lookup"><span data-stu-id="86626-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="86626-127">如果物件未公開您嘗試存取的成員<xref:System.MemberAccessException>發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="86626-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86626-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86626-128">See Also</span></span>  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [<span data-ttu-id="86626-129">物件變數</span><span class="sxs-lookup"><span data-stu-id="86626-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="86626-130">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="86626-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="86626-131">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="86626-131">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="86626-132">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="86626-132">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
