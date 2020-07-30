---
title: 範例 COM 類別 - C# 程式設計指南
description: '瞭解如何在 c # 中以 COM 物件的形式公開類別。 這個範例會將 .cs 檔案中的程式碼加入至專案，並設定 [註冊 COM Interop] 屬性。'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 4ea66ba26595c5bae2e579d1cc85c4b0d58616df
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303032"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="90771-104">範例 COM 類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="90771-104">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="90771-105">以下是公開為 COM 物件類別的範例。</span><span class="sxs-lookup"><span data-stu-id="90771-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="90771-106">在此程式碼放入 .cs 檔案並新增至專案之後，將**註冊 COM Interop** 屬性設定為 **True**。</span><span class="sxs-lookup"><span data-stu-id="90771-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="90771-107">如需詳細資訊，請參閱[如何：註冊 COM Interop 元件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="90771-107">For more information, see [How to: Register a Component for COM Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="90771-108">將 Visual C# 物件公開給 COM 需要宣告類別介面和類別本身，以及事件介面 (若需要)。</span><span class="sxs-lookup"><span data-stu-id="90771-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="90771-109">類別成員必須遵守下列規則才能為 COM 所見︰</span><span class="sxs-lookup"><span data-stu-id="90771-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="90771-110">類別必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="90771-110">The class must be public.</span></span>  
  
- <span data-ttu-id="90771-111">屬性、方法及事件必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="90771-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="90771-112">必須在類別介面上宣告屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="90771-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="90771-113">必須在事件介面中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="90771-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="90771-114">類別中未在這些介面中宣告的其他公用成員將不會顯示在 COM 中，但其他 .NET 物件將會看到它們。</span><span class="sxs-lookup"><span data-stu-id="90771-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="90771-115">若要向 COM 公開屬性和方法，您必須在類別介面上宣告它們，並以 `DispId` 屬性標記它們，然後在類別中實作它們。</span><span class="sxs-lookup"><span data-stu-id="90771-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="90771-116">成員在介面中的宣告順序是 COM vtable 使用的順序。</span><span class="sxs-lookup"><span data-stu-id="90771-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="90771-117">若要從您的類別公開事件，您必須在事件介面上宣告它們，並使用 `DispId` 屬性標記它們。</span><span class="sxs-lookup"><span data-stu-id="90771-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="90771-118">此類別不應該實作這個介面。</span><span class="sxs-lookup"><span data-stu-id="90771-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="90771-119">類別會實作類別介面，它可以實作多個介面，但首次實作是在預設類別介面。</span><span class="sxs-lookup"><span data-stu-id="90771-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="90771-120">實作此處向 COM 公開的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="90771-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="90771-121">它們必須標示為公用，且必須符合類別介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="90771-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="90771-122">此外，宣告類別在此引發的事件。</span><span class="sxs-lookup"><span data-stu-id="90771-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="90771-123">它們必須標示為公用，且必須符合事件介面中的宣告。</span><span class="sxs-lookup"><span data-stu-id="90771-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90771-124">範例</span><span class="sxs-lookup"><span data-stu-id="90771-124">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="90771-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90771-125">See also</span></span>

- [<span data-ttu-id="90771-126">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="90771-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="90771-127">互通性</span><span class="sxs-lookup"><span data-stu-id="90771-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="90771-128">專案設計工具、建置頁 (C#)</span><span class="sxs-lookup"><span data-stu-id="90771-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
