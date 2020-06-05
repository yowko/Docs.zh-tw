---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386954"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="bd9ff-102">類型 \<typename> 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="bd9ff-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="bd9ff-103">變數、屬性或函式傳回宣告的資料類型不符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="bd9ff-104">若要讓應用程式符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）規範，它必須僅使用符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="bd9ff-105">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="bd9ff-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="bd9ff-106">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="bd9ff-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="bd9ff-107">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="bd9ff-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="bd9ff-108">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="bd9ff-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="bd9ff-109">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="bd9ff-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="bd9ff-110">**錯誤識別碼：** BC40041</span><span class="sxs-lookup"><span data-stu-id="bd9ff-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd9ff-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bd9ff-111">To correct this error</span></span>  
  
- <span data-ttu-id="bd9ff-112">如果您的應用程式必須符合 CLS 標準，請將這個元素的資料類型變更為最符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="bd9ff-113">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="bd9ff-114">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="bd9ff-115">如果您的應用程式不需要符合 CLS 標準，您就不需要變更任何專案。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="bd9ff-116">不過，您應該知道它不相容。</span><span class="sxs-lookup"><span data-stu-id="bd9ff-116">You should be aware of its noncompliance, however.</span></span>
