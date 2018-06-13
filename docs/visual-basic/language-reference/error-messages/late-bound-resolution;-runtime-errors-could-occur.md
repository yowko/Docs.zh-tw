---
title: 晚期繫結程序解析; 可能發生執行階段錯誤
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: af027b7752fdf13f1540010a8ddb681182c1b23c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588775"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="f82f7-102">晚期繫結程序解析; 可能發生執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="f82f7-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="f82f7-103">物件變數指派給變數宣告為[物件資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="f82f7-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="f82f7-104">當您將變數宣告為`Object`，編譯器必須執行*晚期繫結*，因而導致執行階段的額外作業。</span><span class="sxs-lookup"><span data-stu-id="f82f7-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="f82f7-105">它也可能會讓您的應用程式發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="f82f7-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="f82f7-106">例如，如果您指派<xref:System.Windows.Forms.Form>至`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>屬性，執行階段會擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別並未公開`NameTable`屬性。</span><span class="sxs-lookup"><span data-stu-id="f82f7-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="f82f7-107">如果是特定類型的變數宣告，編譯器可以執行*早期繫結*在編譯時間。</span><span class="sxs-lookup"><span data-stu-id="f82f7-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="f82f7-108">如此可改善效能、 控制存取特定類型的成員以及您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="f82f7-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="f82f7-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="f82f7-109">By default, this message is a warning.</span></span> <span data-ttu-id="f82f7-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="f82f7-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f82f7-111">**錯誤 ID:** BC42017</span><span class="sxs-lookup"><span data-stu-id="f82f7-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f82f7-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f82f7-112">To correct this error</span></span>  
  
-   <span data-ttu-id="f82f7-113">可能的話，宣告為特定類型的變數。</span><span class="sxs-lookup"><span data-stu-id="f82f7-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82f7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f82f7-114">See Also</span></span>  
 [<span data-ttu-id="f82f7-115">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="f82f7-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="f82f7-116">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="f82f7-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
