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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347342"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="93343-102">Visual Basic 中的 Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="93343-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="93343-103">Visual Basic 中的 `Me`、`My`、`MyBase`和 `MyClass` 具有類似的名稱，但有不同的用途。</span><span class="sxs-lookup"><span data-stu-id="93343-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="93343-104">本主題將說明每個實體，以便加以區別。</span><span class="sxs-lookup"><span data-stu-id="93343-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="93343-105">Me</span><span class="sxs-lookup"><span data-stu-id="93343-105">Me</span></span>  
 <span data-ttu-id="93343-106">`Me` 關鍵字提供了一種方法，可參考程式碼目前執行所在之類別或結構的特定實例。</span><span class="sxs-lookup"><span data-stu-id="93343-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="93343-107">`Me` 的行為就像是參考目前實例的物件變數或結構變數。</span><span class="sxs-lookup"><span data-stu-id="93343-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="93343-108">使用 `Me` 特別適合用來將目前正在執行之類別或結構實例的相關資訊傳遞至另一個類別、結構或模組中的程式。</span><span class="sxs-lookup"><span data-stu-id="93343-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="93343-109">例如，假設您在模組中有下列程式。</span><span class="sxs-lookup"><span data-stu-id="93343-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```vb  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="93343-110">您可以呼叫此程式，並使用下列語句，將 <xref:System.Windows.Forms.Form> 類別的目前實例當做引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="93343-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```vb  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="93343-111">My</span><span class="sxs-lookup"><span data-stu-id="93343-111">My</span></span>  
 <span data-ttu-id="93343-112">`My` 功能可讓您輕鬆且直覺地存取許多 .NET Framework 類別，讓 Visual Basic 的使用者能夠與電腦、應用程式、設定、資源等進行互動。</span><span class="sxs-lookup"><span data-stu-id="93343-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="93343-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="93343-113">MyBase</span></span>  
 <span data-ttu-id="93343-114">`MyBase` 關鍵字的行為就像是參考類別目前實例之基類的物件變數。</span><span class="sxs-lookup"><span data-stu-id="93343-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="93343-115">`MyBase` 通常用來存取在衍生類別中覆寫或遮蔽的基類成員。</span><span class="sxs-lookup"><span data-stu-id="93343-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="93343-116">`MyBase.New` 是用來從衍生類別的函式明確呼叫基類的「自類別」（class）。</span><span class="sxs-lookup"><span data-stu-id="93343-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="93343-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="93343-117">MyClass</span></span>  
 <span data-ttu-id="93343-118">`MyClass` 關鍵字的行為就像是物件變數，其參考原本實作為之類別的目前實例。</span><span class="sxs-lookup"><span data-stu-id="93343-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="93343-119">`MyClass` 類似 `Me`，但會將其上的所有方法呼叫視為已 `NotOverridable`方法。</span><span class="sxs-lookup"><span data-stu-id="93343-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93343-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93343-120">See also</span></span>

- [<span data-ttu-id="93343-121">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="93343-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
