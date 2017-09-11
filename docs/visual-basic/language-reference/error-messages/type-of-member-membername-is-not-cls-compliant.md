---
title: "成員的型別 &quot;&lt;membername&gt;&quot; 不符合 CLS 標準 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
dev_langs:
- VB
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
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
ms.openlocfilehash: ab4d0936603ae133bd7def4341f29d5fcdf7188b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="bc022-102">成員的型別 '&lt;membername&gt;' 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="bc022-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="bc022-103">指定不是這個成員的資料類型屬於[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)。</span><span class="sxs-lookup"><span data-stu-id="bc022-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="bc022-104">這並不在您的元件中發生錯誤，因為[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]和[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]支援這種資料類型。</span><span class="sxs-lookup"><span data-stu-id="bc022-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] support this data type.</span></span> <span data-ttu-id="bc022-105">不過，另一個以嚴格符合 CLS 標準的程式碼撰寫的元件可能不支援此資料型別。</span><span class="sxs-lookup"><span data-stu-id="bc022-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="bc022-106">這類元件可能無法順利與您的元件互動。</span><span class="sxs-lookup"><span data-stu-id="bc022-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="bc022-107">下列 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 資料類型不符合 CLS 規範：</span><span class="sxs-lookup"><span data-stu-id="bc022-107">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="bc022-108">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="bc022-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="bc022-109">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="bc022-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="bc022-110">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="bc022-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="bc022-111">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="bc022-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="bc022-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="bc022-112">By default, this message is a warning.</span></span> <span data-ttu-id="bc022-113">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="bc022-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bc022-114">**錯誤識別碼︰** BC40025</span><span class="sxs-lookup"><span data-stu-id="bc022-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc022-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc022-115">To correct this error</span></span>  
  
-   <span data-ttu-id="bc022-116">如果您的元件介面僅能與其他[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]元件，還是不介面與其他任何元件中，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="bc022-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="bc022-117">如果您要連接的元件不是針對撰寫[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]，您可以判斷，是透過反映或自文件，是否支援此資料型別。</span><span class="sxs-lookup"><span data-stu-id="bc022-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="bc022-118">如果是的話，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="bc022-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="bc022-119">如果您要使用的元件不支援這種資料類型，您必須將它取代最符合 CLS 標準的型別。</span><span class="sxs-lookup"><span data-stu-id="bc022-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="bc022-120">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="bc022-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="bc022-121">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="bc022-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="bc022-122">如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中的資料寬度不同。</span><span class="sxs-lookup"><span data-stu-id="bc022-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="bc022-123">例如，`uint` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="bc022-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="bc022-124">如果您要將 16 位元引數傳遞至這類元件，將它宣告為`UShort`而不是`UInteger`中 managed[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式碼。</span><span class="sxs-lookup"><span data-stu-id="bc022-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc022-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc022-125">See Also</span></span>  
 <span data-ttu-id="bc022-126">[反映](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span><span class="sxs-lookup"><span data-stu-id="bc022-126">[Reflection](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span></span>  
<span data-ttu-id="bc022-127"> [\<PAVE OVER > 撰寫符合 CLS 標準的程式碼](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="bc022-127"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
