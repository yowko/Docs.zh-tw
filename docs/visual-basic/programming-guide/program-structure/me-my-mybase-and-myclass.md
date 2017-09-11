---
title: "Me、 My、 MyBase 和 MyClass 在 Visual Basic |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
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
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3ba634eb28c25f47a0e88c856b916383b6ad15a2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="d6947-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="d6947-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="d6947-103">`Me``My`， `MyBase`，和`MyClass`中[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]有類似的名稱，但不同的用途。</span><span class="sxs-lookup"><span data-stu-id="d6947-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="d6947-104">本主題會描述每個實體才能區分它們。</span><span class="sxs-lookup"><span data-stu-id="d6947-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="d6947-105">Me</span><span class="sxs-lookup"><span data-stu-id="d6947-105">Me</span></span>  
 <span data-ttu-id="d6947-106">`Me`關鍵字可用來參考類別或結構的程式碼目前執行所在的特定執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6947-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="d6947-107">`Me`行為就像物件變數或目前的執行個體參考結構變數。</span><span class="sxs-lookup"><span data-stu-id="d6947-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="d6947-108">使用`Me`特別適用於傳遞至另一個類別、 結構或模組中的程序的類別或結構的目前執行的執行個體的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6947-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="d6947-109">例如，假設您有下列的程序在模組中。</span><span class="sxs-lookup"><span data-stu-id="d6947-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="d6947-110">您可以呼叫此程序，並傳遞目前執行個體<xref:System.Windows.Forms.Form>類別做為引數使用下列陳述式。</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="d6947-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="d6947-111">My</span><span class="sxs-lookup"><span data-stu-id="d6947-111">My</span></span>  
 <span data-ttu-id="d6947-112">`My`功能提供簡單又直覺式存取數個[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別，啟用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用者互動的電腦、 應用程式、 設定、 資源等。</span><span class="sxs-lookup"><span data-stu-id="d6947-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, enabling the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="d6947-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="d6947-113">MyBase</span></span>  
 <span data-ttu-id="d6947-114">`MyBase`關鍵字的行為就像參考類別的目前執行個體的基底類別的物件變數。</span><span class="sxs-lookup"><span data-stu-id="d6947-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="d6947-115">`MyBase`通常用來存取基底類別成員會覆寫或遮蔽衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="d6947-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="d6947-116">`MyBase.New`用來明確地從衍生的類別建構函式呼叫基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="d6947-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="d6947-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="d6947-117">MyClass</span></span>  
 <span data-ttu-id="d6947-118">`MyClass`關鍵字的行為就像原本實作類別的目前執行個體參考的物件變數。</span><span class="sxs-lookup"><span data-stu-id="d6947-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="d6947-119">`MyClass`類似於`Me`，但在其上的所有方法呼叫會都視為方法`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="d6947-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6947-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6947-120">See Also</span></span>  
 [<span data-ttu-id="d6947-121">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="d6947-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
