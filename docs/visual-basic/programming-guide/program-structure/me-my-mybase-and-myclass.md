---
title: Visual Basic 中的 Me、My、MyBase 和 MyClass
ms.date: 07/20/2015
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
ms.openlocfilehash: f3db5f8f6688e68992f683ac1b1465078aa41231
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244708"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="9defc-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="9defc-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="9defc-103">`Me``My`， `MyBase`，和`MyClass`Visual Basic 中有類似的名稱，但不同的用途。</span><span class="sxs-lookup"><span data-stu-id="9defc-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="9defc-104">本主題會描述每個實體以區別。</span><span class="sxs-lookup"><span data-stu-id="9defc-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="9defc-105">Me</span><span class="sxs-lookup"><span data-stu-id="9defc-105">Me</span></span>  
 <span data-ttu-id="9defc-106">`Me`關鍵字可用來參考類別或結構的程式碼目前執行所在的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="9defc-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="9defc-107">`Me` 物件變數或目前的執行個體參考結構變數等的行為。</span><span class="sxs-lookup"><span data-stu-id="9defc-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="9defc-108">使用`Me`特別適用於將目前執行的執行個體的類別或結構的相關資訊傳遞至另一個類別、 結構或模組中的程序。</span><span class="sxs-lookup"><span data-stu-id="9defc-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="9defc-109">例如，假設您有在模組中的下列程序。</span><span class="sxs-lookup"><span data-stu-id="9defc-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="9defc-110">您可以呼叫此程序，並傳遞目前的執行個體<xref:System.Windows.Forms.Form>做為引數使用下列陳述式的類別。</span><span class="sxs-lookup"><span data-stu-id="9defc-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="9defc-111">My</span><span class="sxs-lookup"><span data-stu-id="9defc-111">My</span></span>  
 <span data-ttu-id="9defc-112">`My`功能提供簡單又直覺式存取數個[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]類別，讓 Visual Basic 使用者與電腦、 應用程式、 設定、 資源等等互動。</span><span class="sxs-lookup"><span data-stu-id="9defc-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="9defc-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="9defc-113">MyBase</span></span>  
 <span data-ttu-id="9defc-114">`MyBase`關鍵字的行為就像參考類別的目前執行個體的基底類別的物件變數。</span><span class="sxs-lookup"><span data-stu-id="9defc-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="9defc-115">`MyBase` 通常用來存取所覆寫或遮蔽衍生類別中的基底類別成員。</span><span class="sxs-lookup"><span data-stu-id="9defc-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="9defc-116">`MyBase.New` 用來明確地從衍生的類別建構函式呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="9defc-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="9defc-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="9defc-117">MyClass</span></span>  
 <span data-ttu-id="9defc-118">`MyClass`關鍵字的行為就像參考目前的執行個體的類別，以原始實作的物件變數。</span><span class="sxs-lookup"><span data-stu-id="9defc-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="9defc-119">`MyClass` 類似於`Me`，但在其上的所有方法呼叫會都視為方法`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="9defc-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9defc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9defc-120">See Also</span></span>  
 [<span data-ttu-id="9defc-121">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="9defc-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
