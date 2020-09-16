---
title: 範例 COM 類別 - C# 程式設計指南
description: '瞭解如何在 c # 中將類別公開為 COM 物件。 此範例會將 .cs 檔案中的程式碼加入至專案，並設定 COM Interop 屬性的暫存器。'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: d49d391f5ea7717e0c36782be65cfb2ae154b843
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542792"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="342ff-104">範例 COM 類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="342ff-104">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="342ff-105">以下是公開為 COM 物件類別的範例。</span><span class="sxs-lookup"><span data-stu-id="342ff-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="342ff-106">在此程式碼放入 .cs 檔案並新增至專案之後，將**註冊 COM Interop** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="342ff-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="342ff-107">如需詳細資訊，請參閱[如何：註冊 COM Interop 元件](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="342ff-107">For more information, see [How to: Register a Component for COM Interop](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="342ff-108">將 Visual C# 物件公開給 COM 需要宣告類別介面和類別本身，以及事件介面 (若需要)。</span><span class="sxs-lookup"><span data-stu-id="342ff-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="342ff-109">類別成員必須遵守下列規則才能為 COM 所見︰</span><span class="sxs-lookup"><span data-stu-id="342ff-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="342ff-110">類別必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="342ff-110">The class must be public.</span></span>  
  
- <span data-ttu-id="342ff-111">屬性、方法及事件必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="342ff-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="342ff-112">必須在類別介面上宣告屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="342ff-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="342ff-113">必須在事件介面中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="342ff-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="342ff-114">未在這些介面中宣告之類別中的其他公用成員將不會顯示于 COM 中，但其他 .NET 物件將會顯示這些成員。</span><span class="sxs-lookup"><span data-stu-id="342ff-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="342ff-115">若要向 COM 公開屬性和方法，您必須在類別介面上宣告它們，並以 `DispId` 屬性標記它們，然後在類別中實作它們。</span><span class="sxs-lookup"><span data-stu-id="342ff-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="342ff-116">成員在介面中的宣告順序是 COM vtable 使用的順序。</span><span class="sxs-lookup"><span data-stu-id="342ff-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="342ff-117">若要從您的類別公開事件，您必須在事件介面上宣告它們，並使用 `DispId` 屬性標記它們。</span><span class="sxs-lookup"><span data-stu-id="342ff-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="342ff-118">此類別不應該實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="342ff-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="342ff-119">類別會實作類別介面，它可以實作多個介面，但首次實作是在預設類別介面。</span><span class="sxs-lookup"><span data-stu-id="342ff-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="342ff-120">實作此處向 COM 公開的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="342ff-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="342ff-121">它們必須標示為公用，且必須符合類別介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="342ff-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="342ff-122">此外，宣告類別在此引發的事件。</span><span class="sxs-lookup"><span data-stu-id="342ff-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="342ff-123">它們必須標示為公用，且必須符合事件介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="342ff-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="342ff-124">範例</span><span class="sxs-lookup"><span data-stu-id="342ff-124">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="342ff-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="342ff-125">See also</span></span>

- [<span data-ttu-id="342ff-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="342ff-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="342ff-127">互通性</span><span class="sxs-lookup"><span data-stu-id="342ff-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="342ff-128">專案設計工具、建置頁 (C#)</span><span class="sxs-lookup"><span data-stu-id="342ff-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
