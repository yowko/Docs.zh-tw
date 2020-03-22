---
title: Me、My、MyBase 及 MyClass
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
ms.openlocfilehash: a21dfeb12e8d99f5f8b8afede084846711c299ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400845"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="d4a64-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="d4a64-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="d4a64-103">`Me`、`My``MyBase`和`MyClass`在 Visual Basic 中具有相似的名稱，但目的不同。</span><span class="sxs-lookup"><span data-stu-id="d4a64-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="d4a64-104">本主題介紹每個實體，以便區分它們。</span><span class="sxs-lookup"><span data-stu-id="d4a64-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="d4a64-105">我</span><span class="sxs-lookup"><span data-stu-id="d4a64-105">Me</span></span>  
 <span data-ttu-id="d4a64-106">關鍵字`Me`提供了一種引用代碼當前正在執行的類或結構的特定實例的方法。</span><span class="sxs-lookup"><span data-stu-id="d4a64-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="d4a64-107">`Me`其活動類似于物件變數或引用當前實例的結構變數。</span><span class="sxs-lookup"><span data-stu-id="d4a64-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="d4a64-108">使用`Me`對於將有關類或結構當前執行實例的資訊傳遞給另一個類、結構或模組中的過程特別有用。</span><span class="sxs-lookup"><span data-stu-id="d4a64-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="d4a64-109">例如，假設您在模組中具有以下過程。</span><span class="sxs-lookup"><span data-stu-id="d4a64-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="d4a64-110">可以使用以下語句調用此過程並將<xref:System.Windows.Forms.Form>類的當前實例作為參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="d4a64-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="d4a64-111">My</span><span class="sxs-lookup"><span data-stu-id="d4a64-111">My</span></span>  
 <span data-ttu-id="d4a64-112">此功能`My`提供了對許多 .NET Framework 類的輕鬆直觀訪問，使 Visual Basic 使用者能夠與電腦、應用程式、設置、資源等進行交互。</span><span class="sxs-lookup"><span data-stu-id="d4a64-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="d4a64-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="d4a64-113">MyBase</span></span>  
 <span data-ttu-id="d4a64-114">關鍵字`MyBase`的作用類似于引用類當前實例的基類的物件變數。</span><span class="sxs-lookup"><span data-stu-id="d4a64-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="d4a64-115">`MyBase`通常用於訪問派生類中重寫或隱藏基類成員。</span><span class="sxs-lookup"><span data-stu-id="d4a64-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="d4a64-116">`MyBase.New`用於從派生類建構函式顯式調用基類建構函式。</span><span class="sxs-lookup"><span data-stu-id="d4a64-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="d4a64-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="d4a64-117">MyClass</span></span>  
 <span data-ttu-id="d4a64-118">關鍵字`MyClass`的作用類似于一個物件變數，它引用最初實現的類的當前實例。</span><span class="sxs-lookup"><span data-stu-id="d4a64-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="d4a64-119">`MyClass`與 類似`Me`，但上它的所有方法調用都被視為方法為`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="d4a64-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a64-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4a64-120">See also</span></span>

- [<span data-ttu-id="d4a64-121">繼承基本概念</span><span class="sxs-lookup"><span data-stu-id="d4a64-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
