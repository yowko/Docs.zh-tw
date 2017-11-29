---
title: "型別&lt;typename&gt;不符合 CLS 標準"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d45da3b061dff0f82c1155daf5724033261bbdaa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="4d68d-102">型別&lt;typename&gt;不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="4d68d-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="4d68d-103">具有不符合 CLS 標準的資料類型來宣告變數、 屬性或函式傳回。</span><span class="sxs-lookup"><span data-stu-id="4d68d-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="4d68d-104">若要符合應用程式[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)（cls） 標準，它必須使用只有符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="4d68d-104">For an application to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="4d68d-105">下列 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="4d68d-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="4d68d-106">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d68d-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="4d68d-107">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d68d-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="4d68d-108">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d68d-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="4d68d-109">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="4d68d-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="4d68d-110">**錯誤 ID:** BC40041</span><span class="sxs-lookup"><span data-stu-id="4d68d-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d68d-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4d68d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="4d68d-112">如果您的應用程式必須符合 CLS 標準，變更的資料類型的這個項目為最接近符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="4d68d-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="4d68d-113">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="4d68d-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="4d68d-114">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="4d68d-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="4d68d-115">如果您的應用程式不需要符合 CLS 標準，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="4d68d-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="4d68d-116">您應該注意不相容的問題，不過。</span><span class="sxs-lookup"><span data-stu-id="4d68d-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d68d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d68d-117">See Also</span></span>  
 [<span data-ttu-id="4d68d-118">\<PAVE OVER > 撰寫符合 CLS 標準的程式碼</span><span class="sxs-lookup"><span data-stu-id="4d68d-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
