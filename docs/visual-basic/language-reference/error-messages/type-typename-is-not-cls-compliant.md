---
title: 類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: c50e721e9170a402724a11f3aab573c7e8abf4c1
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161162"
---
# <a name="bc40041-type-typename-is-not-cls-compliant"></a><span data-ttu-id="744b0-102">BC40041：類型 \<typename> 不符合 CLS 規範</span><span class="sxs-lookup"><span data-stu-id="744b0-102">BC40041: Type \<typename> is not CLS-compliant</span></span>

<span data-ttu-id="744b0-103">變數、屬性或函式傳回所宣告的資料類型不符合 CLS 規範。</span><span class="sxs-lookup"><span data-stu-id="744b0-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>

 <span data-ttu-id="744b0-104">若要讓應用程式符合 Language-Independent 的 [語言獨立性和](../../../standard/language-independence-and-language-independent-components.md) (cls) 的元件，它必須只使用符合 cls 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="744b0-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>

 <span data-ttu-id="744b0-105">下列 Visual Basic 資料類型不符合 CLS 規範：</span><span class="sxs-lookup"><span data-stu-id="744b0-105">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="744b0-106">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="744b0-106">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="744b0-107">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="744b0-107">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="744b0-108">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="744b0-108">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="744b0-109">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="744b0-109">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="744b0-110">**錯誤識別碼：** BC40041</span><span class="sxs-lookup"><span data-stu-id="744b0-110">**Error ID:** BC40041</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="744b0-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="744b0-111">To correct this error</span></span>

- <span data-ttu-id="744b0-112">如果您的應用程式必須符合 CLS 規範，請將這個元素的資料類型變更為最接近 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="744b0-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="744b0-113">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="744b0-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="744b0-114">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="744b0-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="744b0-115">如果您的應用程式不需要符合 CLS 標準，您就不需要變更任何變更。</span><span class="sxs-lookup"><span data-stu-id="744b0-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="744b0-116">不過，您應該知道它不符合規範。</span><span class="sxs-lookup"><span data-stu-id="744b0-116">You should be aware of its noncompliance, however.</span></span>
