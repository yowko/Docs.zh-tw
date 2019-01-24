---
title: 晚期繫結程序解析; 可能發生執行階段錯誤
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 9caf02907e4b6de4c2bd8de778d4ad7a9320a82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690575"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="533d8-102">晚期繫結程序解析; 可能發生執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="533d8-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="533d8-103">物件會指派給宣告為變數[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="533d8-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="533d8-104">當您宣告一個變數`Object`，編譯器必須執行*晚期繫結*，這會導致額外的作業在執行階段。</span><span class="sxs-lookup"><span data-stu-id="533d8-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="533d8-105">它也可能會讓您的應用程式發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="533d8-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="533d8-106">比方說，如果您指派<xref:System.Windows.Forms.Form>要`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>屬性，執行階段會擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別並未公開`NameTable`屬性。</span><span class="sxs-lookup"><span data-stu-id="533d8-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="533d8-107">如果您宣告為特定類型的變數，編譯器可以執行*早期繫結*在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="533d8-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="533d8-108">如此可改善效能、 控制存取權的特定型別、 成員和您的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="533d8-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="533d8-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="533d8-109">By default, this message is a warning.</span></span> <span data-ttu-id="533d8-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="533d8-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="533d8-111">**錯誤 ID:** BC42017</span><span class="sxs-lookup"><span data-stu-id="533d8-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="533d8-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="533d8-112">To correct this error</span></span>  
  
-   <span data-ttu-id="533d8-113">可能的話，將特定類型的變數宣告。</span><span class="sxs-lookup"><span data-stu-id="533d8-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="533d8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="533d8-114">See also</span></span>
- [<span data-ttu-id="533d8-115">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="533d8-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="533d8-116">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="533d8-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
