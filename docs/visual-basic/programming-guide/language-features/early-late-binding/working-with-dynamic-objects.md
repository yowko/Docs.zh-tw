---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345168"
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="84fac-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84fac-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="84fac-103">動態物件提供另一種方式，而不是 `Object` 類型，以便在執行時間晚期繫結至物件。</span><span class="sxs-lookup"><span data-stu-id="84fac-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="84fac-104">動態物件會使用 <xref:System.Dynamic> 命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法）。</span><span class="sxs-lookup"><span data-stu-id="84fac-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="84fac-105">您可以使用 <xref:System.Dynamic> 命名空間中的類別來建立物件，以使用不符合靜態類型或格式的資料結構。</span><span class="sxs-lookup"><span data-stu-id="84fac-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="84fac-106">您也可以使用動態語言（例如 IronPython 和 IronRuby）中定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="84fac-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="84fac-107">如需示範如何建立動態物件或使用動態語言中所定義動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、<xref:System.Dynamic.DynamicObject>或 <xref:System.Dynamic.ExpandoObject>。</span><span class="sxs-lookup"><span data-stu-id="84fac-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="84fac-108">Visual Basic 會使用 <xref:System.Dynamic.IDynamicMetaObjectProvider> 介面，從動態語言執行時間和動態語言（例如 IronPython 和 IronRuby）系結至物件。</span><span class="sxs-lookup"><span data-stu-id="84fac-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="84fac-109">執行 `IDynamicMetaObjectProvider` 介面的類別範例包括 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。</span><span class="sxs-lookup"><span data-stu-id="84fac-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="84fac-110">如果對執行 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，Visual Basic 使用該介面系結至動態物件。</span><span class="sxs-lookup"><span data-stu-id="84fac-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="84fac-111">如果對未執行 `IDynamicMetaObjectProvider` 介面的物件進行晚期繫結呼叫，或呼叫 `IDynamicMetaObjectProvider` 介面失敗，Visual Basic 會使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。</span><span class="sxs-lookup"><span data-stu-id="84fac-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84fac-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="84fac-112">See also</span></span>

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [<span data-ttu-id="84fac-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="84fac-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [<span data-ttu-id="84fac-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="84fac-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
