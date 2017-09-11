---
title: "使用動態物件 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d1e1c4f7338daad0f1101f6e886eba6c37316b0e
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="68cc8-102">使用動態物件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68cc8-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="68cc8-103">動態物件以外的其他提供另一種方式，`Object`類型，以在執行階段物件晚期繫結。</span><span class="sxs-lookup"><span data-stu-id="68cc8-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="68cc8-104">動態物件公開 （expose) 成員，例如屬性和方法在執行階段使用動態介面中定義的<xref:System.Dynamic>命名空間。</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="68cc8-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="68cc8-105">您可以使用中的類別<xref:System.Dynamic>命名空間來建立使用靜態型別或格式不相符的資料結構的物件。</xref:System.Dynamic></span><span class="sxs-lookup"><span data-stu-id="68cc8-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="68cc8-106">您也可以使用諸如 IronPython 和 IronRuby 的動態語言中所定義的動態物件。</span><span class="sxs-lookup"><span data-stu-id="68cc8-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="68cc8-107">說明如何建立動態物件，或使用動態物件定義在動態語言的範例，請參閱[逐步解說︰ 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)， <xref:System.Dynamic.DynamicObject>，或<xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="68cc8-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="68cc8-108">繫結至物件的動態語言執行階段和動態語言，例如 IronPython 和 IronRuby 使用<xref:System.Dynamic.IDynamicMetaObjectProvider>介面。</xref:System.Dynamic.IDynamicMetaObjectProvider></span><span class="sxs-lookup"><span data-stu-id="68cc8-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="68cc8-109">實作的類別範例`IDynamicMetaObjectProvider`介面都是<xref:System.Dynamic.DynamicObject>和<xref:System.Dynamic.ExpandoObject>類別。</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="68cc8-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="68cc8-110">如果要實作的物件進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]繫結至動態的物件，使用該介面。</span><span class="sxs-lookup"><span data-stu-id="68cc8-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="68cc8-111">如果物件不會實作進行晚期繫結呼叫`IDynamicMetaObjectProvider`介面，或如果呼叫`IDynamicMetaObjectProvider`介面失敗，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]繫結至物件，使用晚期繫結功能[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]執行階段。</span><span class="sxs-lookup"><span data-stu-id="68cc8-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68cc8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68cc8-112">See Also</span></span>  
 <span data-ttu-id="68cc8-113"><xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="68cc8-113"><xref:System.Dynamic.DynamicObject></span></span>   
 <span data-ttu-id="68cc8-114"><xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject></span><span class="sxs-lookup"><span data-stu-id="68cc8-114"><xref:System.Dynamic.ExpandoObject></span></span>   
<span data-ttu-id="68cc8-115"> [逐步解說︰ 建立和使用動態物件](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span><span class="sxs-lookup"><span data-stu-id="68cc8-115"> [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span></span>  
<span data-ttu-id="68cc8-116"> [早期和晚期繫結](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="68cc8-116"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
