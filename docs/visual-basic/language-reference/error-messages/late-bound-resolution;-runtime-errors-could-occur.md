---
title: 晚期繫結程序解析; 可能發生執行階段錯誤
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397346"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="10a3d-102">晚期繫結程序解析; 可能發生執行階段錯誤</span><span class="sxs-lookup"><span data-stu-id="10a3d-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="10a3d-103">已將物件指派給宣告為[Object 資料類型](../data-types/object-data-type.md)的變數。</span><span class="sxs-lookup"><span data-stu-id="10a3d-103">An object is assigned to a variable declared to be of the [Object Data Type](../data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="10a3d-104">當您將變數宣告為時 `Object` ，編譯器必須執行*晚期繫結*，這會在執行時間造成額外的作業。</span><span class="sxs-lookup"><span data-stu-id="10a3d-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="10a3d-105">它也可能會讓您的應用程式發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="10a3d-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="10a3d-106">例如，如果您將指派 <xref:System.Windows.Forms.Form> 給變數， `Object` 然後嘗試存取 <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> 屬性，則執行時間會擲回， <xref:System.MemberAccessException> 因為類別不 <xref:System.Windows.Forms.Form> 會公開 `NameTable` 屬性。</span><span class="sxs-lookup"><span data-stu-id="10a3d-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="10a3d-107">如果您將變數宣告為特定類型，編譯器可以在編譯時期執行*早期繫結*。</span><span class="sxs-lookup"><span data-stu-id="10a3d-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="10a3d-108">這會改善效能、控制特定類型成員的存取權限，以及更好的程式碼可讀性。</span><span class="sxs-lookup"><span data-stu-id="10a3d-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="10a3d-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="10a3d-109">By default, this message is a warning.</span></span> <span data-ttu-id="10a3d-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="10a3d-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="10a3d-111">**錯誤識別碼：** BC42017</span><span class="sxs-lookup"><span data-stu-id="10a3d-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10a3d-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="10a3d-112">To correct this error</span></span>  
  
- <span data-ttu-id="10a3d-113">可能的話，請將變數宣告為特定類型。</span><span class="sxs-lookup"><span data-stu-id="10a3d-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a3d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a3d-114">See also</span></span>

- [<span data-ttu-id="10a3d-115">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="10a3d-115">Early and Late Binding</span></span>](../../programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="10a3d-116">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="10a3d-116">Object Variable Declaration</span></span>](../../programming-guide/language-features/variables/object-variable-declaration.md)
