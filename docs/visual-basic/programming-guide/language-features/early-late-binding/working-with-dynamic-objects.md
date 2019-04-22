---
title: 使用動態物件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: ea7d7aae1cd79a0243a9c721b5e3958fba82f84f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832069"
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="bd8f8-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd8f8-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="bd8f8-103">動態物件會提供另一種方式，而非`Object`類型，以在執行階段在物件的晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="bd8f8-104">動態物件在執行階段公開成員，例如屬性和方法，藉由使用動態中所定義的介面<xref:System.Dynamic>命名空間。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="bd8f8-105">您可以使用中的類別<xref:System.Dynamic>命名空間，以建立靜態類型或格式不相符的資料結構所使用的物件。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="bd8f8-106">您也可以使用 IronPython 和 IronRuby 之類的動態語言中所定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="bd8f8-107">如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="bd8f8-108">Visual Basic 中的繫結物件的動態語言執行平台和動態語言 IronPython 和 IronRuby 之類使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="bd8f8-109">範例類別可實作`IDynamicMetaObjectProvider`介面會<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="bd8f8-110">如果晚期繫結進行呼叫，以實作的物件`IDynamicMetaObjectProvider`介面，以使用該介面的動態物件的 Visual Basic 繫結。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="bd8f8-111">如果晚期繫結呼叫對物件未實作`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗時，Visual Basic 繫結至物件所使用的 Visual Basic 執行階段的晚期繫結功能。</span><span class="sxs-lookup"><span data-stu-id="bd8f8-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8f8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd8f8-112">See also</span></span>

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [<span data-ttu-id="bd8f8-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="bd8f8-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [<span data-ttu-id="bd8f8-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="bd8f8-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
