---
title: "晚期繫結的解析;可能發生執行階段錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
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
ms.openlocfilehash: 3baf28a17077d255b42f38ade21ce6153c24e862
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="d6cc4-102">晚期繫結程序解析; 可能發生執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="d6cc4-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="d6cc4-103">在物件指派給變數宣告為[Object 資料型別](../../../visual-basic/language-reference/data-types/object-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="d6cc4-104">當您將變數宣告為`Object`，編譯器必須執行*晚期繫結*，而導致額外的作業在執行階段。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="d6cc4-105">它也可能會讓您的應用程式發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="d6cc4-106">例如，如果您指派<xref:System.Windows.Forms.Form>至`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>屬性，在執行階段擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別不會公開`NameTable`屬性。</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="d6cc4-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="d6cc4-107">如果是特定類型的變數宣告，編譯器可以執行*早期繫結*在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="d6cc4-108">如此可改善效能，控制存取的特定型別、 成員以及您的程式碼更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="d6cc4-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-109">By default, this message is a warning.</span></span> <span data-ttu-id="d6cc4-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d6cc4-111">**錯誤識別碼︰** BC42017</span><span class="sxs-lookup"><span data-stu-id="d6cc4-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6cc4-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d6cc4-112">To correct this error</span></span>  
  
-   <span data-ttu-id="d6cc4-113">可能的話，請宣告為特定類型的變數。</span><span class="sxs-lookup"><span data-stu-id="d6cc4-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cc4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6cc4-114">See Also</span></span>  
 <span data-ttu-id="d6cc4-115">[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="d6cc4-115">[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="d6cc4-116"> [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="d6cc4-116"> [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span></span>
