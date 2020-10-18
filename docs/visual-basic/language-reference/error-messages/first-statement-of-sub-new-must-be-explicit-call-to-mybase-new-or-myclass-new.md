---
title: "這個 'Sub New' 的第一個陳述式必須是對 'MyBase.New' 或 'MyClass.New' 的明確呼叫，因為 '<constructorname>' 的基底類別 '<baseclassname>' 中的 '<derivedclassname>' 標記為過時: '<errormessage>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30920
- bc30920
helpviewer_keywords:
- BC30920
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
ms.openlocfilehash: 4b927e3eed8f9d7f46255b907342465f48263724
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163034"
---
# <a name="bc30920-first-statement-of-this-sub-new-must-be-an-explicit-call-to-mybasenew-or-myclassnew-because-the-constructorname-in-the-base-class-baseclassname-of-derivedclassname-is-marked-obsolete-errormessage"></a><span data-ttu-id="70b9b-102">BC30920：這個 ' Sub New ' 的第一個語句必須是對 ' MyBase. New ' 或 ' MyClass. New ' 的明確呼叫，因為 \<constructorname> ' ' 的基類 ' ' 中的 ' ' \<baseclassname> \<derivedclassname> 已標記為過時： ' \<errormessage> '</span><span class="sxs-lookup"><span data-stu-id="70b9b-102">BC30920: First statement of this 'Sub New' must be an explicit call to 'MyBase.New' or 'MyClass.New' because the '\<constructorname>' in the base class '\<baseclassname>' of '\<derivedclassname>' is marked obsolete: '\<errormessage>'</span></span>

<span data-ttu-id="70b9b-103">類別建構函式未明確地呼叫基底類別建構函式，而且隱含的基底類別建構函式已使用 <xref:System.ObsoleteAttribute> 屬性和指示詞標記，以將其視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="70b9b-103">A class constructor does not explicitly call a base class constructor, and the implicit base class constructor is marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as an error.</span></span>

 <span data-ttu-id="70b9b-104">當衍生類別的函式未呼叫基類的函式時，Visual Basic 會嘗試產生無參數基類的函式的隱含呼叫。</span><span class="sxs-lookup"><span data-stu-id="70b9b-104">When a derived class constructor does not call a base class constructor, Visual Basic attempts to generate an implicit call to a parameterless base class constructor.</span></span> <span data-ttu-id="70b9b-105">如果沒有引數即可呼叫的基類中沒有可存取的函式，Visual Basic 無法產生隱含呼叫。</span><span class="sxs-lookup"><span data-stu-id="70b9b-105">If there is no accessible constructor in the base class that can be called without arguments, Visual Basic cannot generate an implicit call.</span></span> <span data-ttu-id="70b9b-106">在此情況下，必要的函式會以 <xref:System.ObsoleteAttribute> 屬性標記，因此 Visual Basic 無法呼叫它。</span><span class="sxs-lookup"><span data-stu-id="70b9b-106">In this case, the required constructor is marked with the <xref:System.ObsoleteAttribute> attribute, so Visual Basic cannot call it.</span></span>

 <span data-ttu-id="70b9b-107">您可以將任何程式設計項目標記為不再使用，方法是對其套用 <xref:System.ObsoleteAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="70b9b-107">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="70b9b-108">如果您這麼做，則可以將屬性 (attribute) 的 <xref:System.ObsoleteAttribute.IsError%2A> 屬性 (property) 設定為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="70b9b-108">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="70b9b-109">如果您將它設定為 `True`，則編譯器會將使用這個項目的嘗試視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="70b9b-109">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="70b9b-110">如果您將它設定為 `False`，或讓它預設為 `False`，則在嘗試使用該項目時，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="70b9b-110">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>

 <span data-ttu-id="70b9b-111">**錯誤識別碼：** BC30920</span><span class="sxs-lookup"><span data-stu-id="70b9b-111">**Error ID:** BC30920</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="70b9b-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="70b9b-112">To correct this error</span></span>

1. <span data-ttu-id="70b9b-113">請檢查引用的錯誤訊息，並採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="70b9b-113">Examine the quoted error message and take appropriate action.</span></span>

2. <span data-ttu-id="70b9b-114">包含 `MyBase.New()` 或 `MyClass.New()` 的呼叫作為衍生類別中 `Sub New` 的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="70b9b-114">Include a call to `MyBase.New()` or `MyClass.New()` as the first statement of the `Sub New` in the derived class.</span></span>

## <a name="see-also"></a><span data-ttu-id="70b9b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70b9b-115">See also</span></span>

- [<span data-ttu-id="70b9b-116">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="70b9b-116">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
