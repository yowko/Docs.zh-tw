---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 243f51b3e6c798c82fdbe7b28557c4f96c728bf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764370"
---
# <a name="type-typename-is-not-cls-compliant"></a><span data-ttu-id="09292-102">型別\<類型名稱 > 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="09292-102">Type \<typename> is not CLS-compliant</span></span>
<span data-ttu-id="09292-103">使用不符合 CLS 標準的資料類型來宣告變數、 屬性或函式傳回。</span><span class="sxs-lookup"><span data-stu-id="09292-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="09292-104">若要符合應用程式[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準，它必須使用只有符合 CLS 規範的型別。</span><span class="sxs-lookup"><span data-stu-id="09292-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="09292-105">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="09292-105">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="09292-106">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="09292-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="09292-107">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="09292-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="09292-108">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="09292-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="09292-109">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="09292-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="09292-110">**錯誤 ID:** BC40041</span><span class="sxs-lookup"><span data-stu-id="09292-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09292-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="09292-111">To correct this error</span></span>  
  
- <span data-ttu-id="09292-112">如果您的應用程式必須符合 CLS 標準，變更資料類型的這個項目以最符合 CLS 規範的型別。</span><span class="sxs-lookup"><span data-stu-id="09292-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="09292-113">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="09292-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="09292-114">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="09292-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="09292-115">如果您的應用程式不需要符合 CLS 標準，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="09292-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="09292-116">您應留意其不符合規範，不過。</span><span class="sxs-lookup"><span data-stu-id="09292-116">You should be aware of its noncompliance, however.</span></span>