---
title: "使用動態物件 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="81fd2-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81fd2-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="81fd2-103">動態物件會提供另一種方法，除了`Object`類型，以在執行階段物件晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="81fd2-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="81fd2-104">動態物件成員，例如屬性和方法在執行階段會使用公開中所定義的動態介面<xref:System.Dynamic>命名空間。</span><span class="sxs-lookup"><span data-stu-id="81fd2-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="81fd2-105">您可以使用中的類別<xref:System.Dynamic>命名空間，以建立使用的靜態類型或格式不相符的資料結構的物件。</span><span class="sxs-lookup"><span data-stu-id="81fd2-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="81fd2-106">您也可以使用動態語言，例如 IronPython 和 IronRuby 中所定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="81fd2-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="81fd2-107">如需示範如何建立動態物件，或使用動態語言所定義的動態物件的範例，請參閱[逐步解說： 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>。</span><span class="sxs-lookup"><span data-stu-id="81fd2-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="81fd2-108">將其使用的繫結至物件從動態語言執行階段及動態的語言，例如 IronPython 和 IronRuby<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。</span><span class="sxs-lookup"><span data-stu-id="81fd2-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="81fd2-109">類別實作的範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。</span><span class="sxs-lookup"><span data-stu-id="81fd2-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="81fd2-110">如果物件實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使用該介面的繫結的動態物件。</span><span class="sxs-lookup"><span data-stu-id="81fd2-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="81fd2-111">如果物件未實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使用晚期繫結功能的繫結至物件[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="81fd2-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fd2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81fd2-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="81fd2-113">逐步解說：建立和使用動態物件</span><span class="sxs-lookup"><span data-stu-id="81fd2-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="81fd2-114">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="81fd2-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
