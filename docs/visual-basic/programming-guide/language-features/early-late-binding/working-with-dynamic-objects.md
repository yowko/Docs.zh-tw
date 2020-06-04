---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 13b7c80537700c934dbb807b0f264218357088ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405166"
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="98233-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98233-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="98233-103">動態物件提供另一種方法，而不是 `Object` 類型，以便在執行時間晚期系結至物件。</span><span class="sxs-lookup"><span data-stu-id="98233-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="98233-104">動態物件會使用命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法） <xref:System.Dynamic> 。</span><span class="sxs-lookup"><span data-stu-id="98233-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="98233-105">您可以使用命名空間中的類別 <xref:System.Dynamic> 來建立物件，以使用不符合靜態類型或格式的資料結構。</span><span class="sxs-lookup"><span data-stu-id="98233-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="98233-106">您也可以使用動態語言（例如 IronPython 和 IronRuby）中定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="98233-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="98233-107">如需示範如何建立動態物件或使用動態語言中所定義動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject> 或 <xref:System.Dynamic.ExpandoObject> 。</span><span class="sxs-lookup"><span data-stu-id="98233-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="98233-108">Visual Basic 會使用介面，從動態語言執行時間和動態語言（例如 IronPython 和 IronRuby）系結至物件 <xref:System.Dynamic.IDynamicMetaObjectProvider> 。</span><span class="sxs-lookup"><span data-stu-id="98233-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="98233-109">執行介面的類別範例 `IDynamicMetaObjectProvider` 包括 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。</span><span class="sxs-lookup"><span data-stu-id="98233-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="98233-110">如果對執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，Visual Basic 會使用該介面來系結至動態物件。</span><span class="sxs-lookup"><span data-stu-id="98233-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="98233-111">如果對未執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，或介面的呼叫 `IDynamicMetaObjectProvider` 失敗，Visual Basic 會使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。</span><span class="sxs-lookup"><span data-stu-id="98233-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98233-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98233-112">See also</span></span>

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [<span data-ttu-id="98233-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="98233-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [<span data-ttu-id="98233-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="98233-114">Early and Late Binding</span></span>](index.md)
