---
title: 使用動態物件
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 45f8b5c327d40f93b59c2115c75b3b7d385f5a8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057919"
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="11be1-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11be1-102">Working with Dynamic Objects (Visual Basic)</span></span>

<span data-ttu-id="11be1-103">動態物件提供的另一種方式是在 `Object` 執行時間晚期繫結至物件，而非類型。</span><span class="sxs-lookup"><span data-stu-id="11be1-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="11be1-104">動態物件會使用命名空間中定義的動態介面，在執行時間公開成員（例如屬性和方法） <xref:System.Dynamic> 。</span><span class="sxs-lookup"><span data-stu-id="11be1-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="11be1-105">您可以使用命名空間中的類別， <xref:System.Dynamic> 來建立使用不符合靜態類型或格式之資料結構的物件。</span><span class="sxs-lookup"><span data-stu-id="11be1-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="11be1-106">您也可以使用動態物件（例如 IronPython 和 IronRuby）中所定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="11be1-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="11be1-107">如需示範如何建立動態物件或使用動態語言所定義動態物件的範例，請參閱 [逐步解說：建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject> 或 <xref:System.Dynamic.ExpandoObject> 。</span><span class="sxs-lookup"><span data-stu-id="11be1-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="11be1-108">Visual Basic 使用介面系結至動態語言執行時間中的物件和動態語言（例如 IronPython 和 IronRuby） <xref:System.Dynamic.IDynamicMetaObjectProvider> 。</span><span class="sxs-lookup"><span data-stu-id="11be1-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="11be1-109">執行介面之類別的範例 `IDynamicMetaObjectProvider` 為 <xref:System.Dynamic.DynamicObject> 和 <xref:System.Dynamic.ExpandoObject> 類別。</span><span class="sxs-lookup"><span data-stu-id="11be1-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="11be1-110">如果對執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，Visual Basic 使用該介面系結至動態物件。</span><span class="sxs-lookup"><span data-stu-id="11be1-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="11be1-111">如果對未執行介面的物件進行晚期繫結呼叫 `IDynamicMetaObjectProvider` ，或對介面的呼叫 `IDynamicMetaObjectProvider` 失敗，Visual Basic 使用 Visual Basic 執行時間的晚期繫結功能來系結至物件。</span><span class="sxs-lookup"><span data-stu-id="11be1-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11be1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11be1-112">See also</span></span>

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [<span data-ttu-id="11be1-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="11be1-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [<span data-ttu-id="11be1-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="11be1-114">Early and Late Binding</span></span>](index.md)
