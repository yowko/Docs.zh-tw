---
title: 使用動態物件 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f00c57107da5e6ea428e14964d8fa4a870bc96c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="eb2e9-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb2e9-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="eb2e9-103">動態物件會提供另一種方法，除了`Object`類型，以在執行階段物件晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="eb2e9-104">動態物件成員，例如屬性和方法在執行階段會使用公開中所定義的動態介面<xref:System.Dynamic>命名空間。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="eb2e9-105">您可以使用中的類別<xref:System.Dynamic>命名空間，以建立使用的靜態類型或格式不相符的資料結構的物件。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="eb2e9-106">您也可以使用動態語言，例如 IronPython 和 IronRuby 中所定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="eb2e9-107">如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說： 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 <span data-ttu-id="eb2e9-108">Visual Basic 中的繫結物件的動態語言執行階段和動態的語言，例如 IronPython 和 IronRuby 使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-108">Visual Basic binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="eb2e9-109">類別實作的範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="eb2e9-110">如果物件實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面、 Visual Basic 繫結到使用該介面的動態物件。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, Visual Basic binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="eb2e9-111">如果物件未實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗時，使用 Visual Basic 執行階段的晚期繫結功能的 Visual Basic 繫結至物件。</span><span class="sxs-lookup"><span data-stu-id="eb2e9-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, Visual Basic binds to the object by using the late-binding capabilities of the Visual Basic runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb2e9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb2e9-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="eb2e9-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="eb2e9-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="eb2e9-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="eb2e9-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
