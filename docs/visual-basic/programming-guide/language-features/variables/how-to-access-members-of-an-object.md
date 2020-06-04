---
title: 如何：存取物件的成員
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 2826a3c98b9f19b08cc943d0f67cdd34ac90f526
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410538"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a><span data-ttu-id="b32b5-102">如何：存取物件的成員 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b32b5-102">How to: Access Members of an Object (Visual Basic)</span></span>

<span data-ttu-id="b32b5-103">當您有參考物件的物件變數時，您通常會想要使用該物件的成員，例如其方法、屬性、欄位和事件。</span><span class="sxs-lookup"><span data-stu-id="b32b5-103">When you have an object variable that refers to an object, you often want to work with the members of that object, such as its methods, properties, fields, and events.</span></span> <span data-ttu-id="b32b5-104">例如，建立新的 <xref:System.Windows.Forms.Form> 物件之後，您可能會想要設定其 <xref:System.Windows.Forms.Control.Text%2A> 屬性或呼叫其 <xref:System.Windows.Forms.Control.Focus%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b32b5-104">For example, once you have created a new <xref:System.Windows.Forms.Form> object, you might want to set its <xref:System.Windows.Forms.Control.Text%2A> property or call its <xref:System.Windows.Forms.Control.Focus%2A> method.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="b32b5-105">存取成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-105">Accessing Members</span></span>

<span data-ttu-id="b32b5-106">您可以透過參考它的變數來存取物件的成員。</span><span class="sxs-lookup"><span data-stu-id="b32b5-106">You access an object's members through the variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object"></a><span data-ttu-id="b32b5-107">存取物件的成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-107">To access members of an object</span></span>

- <span data-ttu-id="b32b5-108">`.`在物件變數名稱和成員名稱之間使用成員存取運算子（）。</span><span class="sxs-lookup"><span data-stu-id="b32b5-108">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    currentText = newForm.Text
    ```

    <span data-ttu-id="b32b5-109">如果成員是[共用](../../../language-reference/modifiers/shared.md)的，您就不需要變數來存取它。</span><span class="sxs-lookup"><span data-stu-id="b32b5-109">If the member is [Shared](../../../language-reference/modifiers/shared.md), you do not need a variable to access it.</span></span>

## <a name="accessing-members-of-an-object-of-known-type"></a><span data-ttu-id="b32b5-110">存取已知型別之物件的成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-110">Accessing Members of an Object of Known Type</span></span>

<span data-ttu-id="b32b5-111">如果您在編譯時期知道物件的類型，您可以針對參考它的變數使用*早期繫結*。</span><span class="sxs-lookup"><span data-stu-id="b32b5-111">If you know the type of an object at compile time, you can use *early binding* for a variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a><span data-ttu-id="b32b5-112">存取您在編譯時期知道型別之物件的成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-112">To access members of an object for which you know the type at compile time</span></span>

1. <span data-ttu-id="b32b5-113">將物件變數宣告為您想要指派給變數之物件的型別。</span><span class="sxs-lookup"><span data-stu-id="b32b5-113">Declare the object variable to be of the type of the object you intend to assign to the variable.</span></span>

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    <span data-ttu-id="b32b5-114">使用 `Option Strict On` ，您只能將 <xref:System.Windows.Forms.Form> 物件（或衍生自之類型的物件 <xref:System.Windows.Forms.Form> ）指派給 `extraForm` 。</span><span class="sxs-lookup"><span data-stu-id="b32b5-114">With `Option Strict On`, you can assign only <xref:System.Windows.Forms.Form> objects (or objects of a type derived from <xref:System.Windows.Forms.Form>) to `extraForm`.</span></span> <span data-ttu-id="b32b5-115">如果您已定義將擴輾轉換為的類別或結構 `CType` <xref:System.Windows.Forms.Form> ，您也可以將該類別或結構指派給 `extraForm` 。</span><span class="sxs-lookup"><span data-stu-id="b32b5-115">If you have defined a class or structure with a widening `CType` conversion to <xref:System.Windows.Forms.Form>, you can also assign that class or structure to `extraForm`.</span></span>

2. <span data-ttu-id="b32b5-116">`.`在物件變數名稱和成員名稱之間使用成員存取運算子（）。</span><span class="sxs-lookup"><span data-stu-id="b32b5-116">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    extraForm.Show()
    ```

    <span data-ttu-id="b32b5-117">不論設定為何，您都可以存取類別特定的所有方法和屬性 <xref:System.Windows.Forms.Form> `Option Strict` 。</span><span class="sxs-lookup"><span data-stu-id="b32b5-117">You can access all of the methods and properties specific to the <xref:System.Windows.Forms.Form> class, no matter what the `Option Strict` setting is.</span></span>

## <a name="accessing-members-of-an-object-of-unknown-type"></a><span data-ttu-id="b32b5-118">存取未知類型物件的成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-118">Accessing Members of an Object of Unknown Type</span></span>

<span data-ttu-id="b32b5-119">如果您在編譯時期不知道物件的型別，則必須針對參考它的任何變數使用*晚期繫結*。</span><span class="sxs-lookup"><span data-stu-id="b32b5-119">If you do not know the type of an object at compile time, you must use *late binding* for any variable that refers to it.</span></span>

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a><span data-ttu-id="b32b5-120">若要存取在編譯時期不知道型別之物件的成員</span><span class="sxs-lookup"><span data-stu-id="b32b5-120">To access members of an object for which you do not know the type at compile time</span></span>

1. <span data-ttu-id="b32b5-121">將物件變數宣告為[物件資料類型](../../../language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="b32b5-121">Declare the object variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="b32b5-122">（宣告變數的方式與 `Object` 將它宣告為一樣 <xref:System.Object?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="b32b5-122">(Declaring a variable as `Object` is the same as declaring it as <xref:System.Object?displayProperty=nameWithType>.)</span></span>

    ```vb
    Dim someControl As Object
    ```

    <span data-ttu-id="b32b5-123">有了 `Option Strict On` ，您就只能存取在類別上定義的成員 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="b32b5-123">With `Option Strict On`, you can access only the members that are defined on the <xref:System.Object> class.</span></span>

2. <span data-ttu-id="b32b5-124">`.`在物件變數名稱和成員名稱之間使用成員存取運算子（）。</span><span class="sxs-lookup"><span data-stu-id="b32b5-124">Use the member-access operator (`.`) between the object variable name and the member name.</span></span>

    ```vb
    someControl.GetType()
    ```

    <span data-ttu-id="b32b5-125">若要能夠存取您指派給物件變數之任何物件的成員，您必須設定 `Option Strict Off` 。</span><span class="sxs-lookup"><span data-stu-id="b32b5-125">To be able to access the members of any object you assign to the object variable, you must set `Option Strict Off`.</span></span> <span data-ttu-id="b32b5-126">當您這麼做時，編譯器無法保證指定的成員是由您指派給變數的物件所公開。</span><span class="sxs-lookup"><span data-stu-id="b32b5-126">When you do this, the compiler cannot guarantee that a given member is exposed by the object you assign to the variable.</span></span> <span data-ttu-id="b32b5-127">如果物件未公開您嘗試存取的成員， <xref:System.MemberAccessException> 就會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b32b5-127">If the object does not expose a member you attempt to access, a <xref:System.MemberAccessException> exception occurs.</span></span>

## <a name="see-also"></a><span data-ttu-id="b32b5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b32b5-128">See also</span></span>

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [<span data-ttu-id="b32b5-129">物件變數</span><span class="sxs-lookup"><span data-stu-id="b32b5-129">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="b32b5-130">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="b32b5-130">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="b32b5-131">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="b32b5-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="b32b5-132">Long</span><span class="sxs-lookup"><span data-stu-id="b32b5-132">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
