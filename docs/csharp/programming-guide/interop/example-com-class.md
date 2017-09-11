---
title: "範例 COM 類別 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a759a7dcd211207c8740dd99d592daa509ddec47
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="81eb5-102">範例 COM 類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="81eb5-102">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="81eb5-103">以下是公開為 COM 物件類別的範例。</span><span class="sxs-lookup"><span data-stu-id="81eb5-103">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="81eb5-104">在此程式碼放入 .cs 檔案並新增至專案之後，將**註冊 COM Interop** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="81eb5-104">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="81eb5-105">如需詳細資訊，請參閱 [NIB：如何：登錄 COM Interop 元件](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e)。</span><span class="sxs-lookup"><span data-stu-id="81eb5-105">For more information, see [NIB: How to: Register a Component for COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).</span></span>  
  
 <span data-ttu-id="81eb5-106">將 Visual C# 物件公開給 COM 需要宣告類別介面和類別本身，以及事件介面 (若需要)。</span><span class="sxs-lookup"><span data-stu-id="81eb5-106">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="81eb5-107">類別成員必須遵守下列規則才能為 COM 所見︰</span><span class="sxs-lookup"><span data-stu-id="81eb5-107">Class members must follow these rules to be visible to COM:</span></span>  
  
-   <span data-ttu-id="81eb5-108">類別必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="81eb5-108">The class must be public.</span></span>  
  
-   <span data-ttu-id="81eb5-109">屬性、方法及事件必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="81eb5-109">Properties, methods, and events must be public.</span></span>  
  
-   <span data-ttu-id="81eb5-110">必須在類別介面上宣告屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="81eb5-110">Properties and methods must be declared on the class interface.</span></span>  
  
-   <span data-ttu-id="81eb5-111">必須在事件介面中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="81eb5-111">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="81eb5-112">未在這些介面中宣告的類別其他公用成員不會為 COM 所見，但會向其他 .NET Framework 物件顯示。</span><span class="sxs-lookup"><span data-stu-id="81eb5-112">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET Framework objects.</span></span>  
  
 <span data-ttu-id="81eb5-113">若要向 COM 公開屬性和方法，您必須在類別介面上宣告它們，並以 `DispId` 屬性標記它們，然後在類別中實作它們。</span><span class="sxs-lookup"><span data-stu-id="81eb5-113">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="81eb5-114">成員在介面中的宣告順序是 COM vtable 使用的順序。</span><span class="sxs-lookup"><span data-stu-id="81eb5-114">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="81eb5-115">若要從您的類別公開事件，您必須在事件介面上宣告它們，並使用 `DispId` 屬性標記它們。</span><span class="sxs-lookup"><span data-stu-id="81eb5-115">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="81eb5-116">此類別不應該實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="81eb5-116">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="81eb5-117">類別會實作類別介面，它可以實作多個介面，但首次實作是在預設類別介面。</span><span class="sxs-lookup"><span data-stu-id="81eb5-117">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="81eb5-118">實作此處向 COM 公開的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="81eb5-118">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="81eb5-119">它們必須標示為公用，且必須符合類別介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="81eb5-119">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="81eb5-120">此外，宣告類別在此引發的事件。</span><span class="sxs-lookup"><span data-stu-id="81eb5-120">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="81eb5-121">它們必須標示為公用，且必須符合事件介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="81eb5-121">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81eb5-122">範例</span><span class="sxs-lookup"><span data-stu-id="81eb5-122">Example</span></span>  
 <span data-ttu-id="81eb5-123">[!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="81eb5-123">[!code-cs[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81eb5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81eb5-124">See Also</span></span>  
 <span data-ttu-id="81eb5-125">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="81eb5-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="81eb5-126">[互通性](../../../csharp/programming-guide/interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="81eb5-126">[Interoperability](../../../csharp/programming-guide/interop/index.md) </span></span>  
 [<span data-ttu-id="81eb5-127">專案設計工具、建置頁面 (C#)</span><span class="sxs-lookup"><span data-stu-id="81eb5-127">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)

