---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 369516fb12b24981eaecfe467bf421dec279aa01
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875091"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="f2ff4-102">類型 \<typename> 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="f2ff4-102">Type \<typename> is not CLS-compliant</span></span>

<span data-ttu-id="f2ff4-103">變數、屬性或函式傳回所宣告的資料類型不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="f2ff4-104">若要讓應用程式符合 [語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md) (cls) ，它必須只使用符合 cls 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="f2ff4-105">下列 Visual Basic 資料類型不符合 CLS 規範：</span><span class="sxs-lookup"><span data-stu-id="f2ff4-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="f2ff4-106">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="f2ff4-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="f2ff4-107">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="f2ff4-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="f2ff4-108">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="f2ff4-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="f2ff4-109">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="f2ff4-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="f2ff4-110">**錯誤識別碼：** BC40041</span><span class="sxs-lookup"><span data-stu-id="f2ff4-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2ff4-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f2ff4-111">To correct this error</span></span>  
  
- <span data-ttu-id="f2ff4-112">如果您的應用程式必須符合 CLS 規範，請將這個元素的資料類型變更為最接近 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="f2ff4-113">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="f2ff4-114">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="f2ff4-115">如果您的應用程式不需要符合 CLS 標準，您就不需要變更任何變更。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="f2ff4-116">不過，您應該知道它不符合規範。</span><span class="sxs-lookup"><span data-stu-id="f2ff4-116">You should be aware of its noncompliance, however.</span></span>
