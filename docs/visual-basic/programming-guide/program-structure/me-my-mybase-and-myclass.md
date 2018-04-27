---
title: Visual Basic 中的 Me、My、MyBase 和 MyClass
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d06c97bdf4824e878d617b2d09993d18c60336b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="caad8-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="caad8-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="caad8-103">`Me``My`， `MyBase`，和`MyClass`在 Visual Basic 中有類似的名稱，但不同的用途。</span><span class="sxs-lookup"><span data-stu-id="caad8-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="caad8-104">本主題會描述每個實體以加以區別。</span><span class="sxs-lookup"><span data-stu-id="caad8-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="caad8-105">Me</span><span class="sxs-lookup"><span data-stu-id="caad8-105">Me</span></span>  
 <span data-ttu-id="caad8-106">`Me`關鍵字可用來參考類別或結構中的目前執行程式碼的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="caad8-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="caad8-107">`Me` 行為類似的物件變數或目前的執行個體參考結構變數。</span><span class="sxs-lookup"><span data-stu-id="caad8-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="caad8-108">使用`Me`將類別或結構的目前執行的執行個體的相關資訊傳遞至另一個類別、 結構或模組中的程序特別有用。</span><span class="sxs-lookup"><span data-stu-id="caad8-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="caad8-109">例如，假設您有下列程序在模組中。</span><span class="sxs-lookup"><span data-stu-id="caad8-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="caad8-110">您可以呼叫此程序，並傳遞目前的執行個體<xref:System.Windows.Forms.Form>做為引數可以使用下列陳述式的類別。</span><span class="sxs-lookup"><span data-stu-id="caad8-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="caad8-111">My</span><span class="sxs-lookup"><span data-stu-id="caad8-111">My</span></span>  
 <span data-ttu-id="caad8-112">`My`功能可讓您容易、 淺顯易懂的存取數目[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別，讓 Visual Basic 使用者互動的電腦、 應用程式、 設定、 資源和等等。</span><span class="sxs-lookup"><span data-stu-id="caad8-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="caad8-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="caad8-113">MyBase</span></span>  
 <span data-ttu-id="caad8-114">`MyBase`關鍵字的行為就像參考目前的執行個體類別的基底類別的物件變數。</span><span class="sxs-lookup"><span data-stu-id="caad8-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="caad8-115">`MyBase` 通常用來存取基底類別成員會覆寫或遮蔽衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="caad8-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="caad8-116">`MyBase.New` 用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="caad8-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="caad8-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="caad8-117">MyClass</span></span>  
 <span data-ttu-id="caad8-118">`MyClass`關鍵字的行為就像以原始實作類別的目前執行個體參考的物件變數。</span><span class="sxs-lookup"><span data-stu-id="caad8-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="caad8-119">`MyClass` 類似於`Me`，但其上的所有方法呼叫會都視為方法`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="caad8-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caad8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caad8-120">See Also</span></span>  
 [<span data-ttu-id="caad8-121">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="caad8-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
