---
title: 成員 '<membername>' 的類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: 9b23ebca955d961771b194df2c7316cb1b7f4a50
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254089"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="80a5f-102">成員的型別 '\<成員名稱 >' 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="80a5f-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="80a5f-103">指定不是這個成員的資料類型的一部分[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。</span><span class="sxs-lookup"><span data-stu-id="80a5f-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="80a5f-104">這是不在您的元件中發生錯誤，因為[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]和 Visual Basic 支援這種資料類型。</span><span class="sxs-lookup"><span data-stu-id="80a5f-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="80a5f-105">不過，另一個以完全符合 CLS 標準的程式碼撰寫的元件可能不支援這種資料類型。</span><span class="sxs-lookup"><span data-stu-id="80a5f-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="80a5f-106">這類元件可能無法順利與您的元件互動。</span><span class="sxs-lookup"><span data-stu-id="80a5f-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="80a5f-107">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="80a5f-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="80a5f-108">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="80a5f-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="80a5f-109">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="80a5f-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="80a5f-110">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="80a5f-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="80a5f-111">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="80a5f-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="80a5f-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="80a5f-112">By default, this message is a warning.</span></span> <span data-ttu-id="80a5f-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="80a5f-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="80a5f-114">**錯誤 ID:** BC40025</span><span class="sxs-lookup"><span data-stu-id="80a5f-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80a5f-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="80a5f-115">To correct this error</span></span>  
  
-   <span data-ttu-id="80a5f-116">如果您的元件介面只能與其他[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]元件或不與任何其他元件互動，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="80a5f-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="80a5f-117">如果您要連接與元件不是針對撰寫[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]，您可以判斷，可能是透過反映或文件，是否支援此資料類型。</span><span class="sxs-lookup"><span data-stu-id="80a5f-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="80a5f-118">若是如此，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="80a5f-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="80a5f-119">如果您要使用的元件不支援這種資料類型，您必須將它取代最符合 CLS 規範的型別。</span><span class="sxs-lookup"><span data-stu-id="80a5f-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="80a5f-120">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="80a5f-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="80a5f-121">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="80a5f-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="80a5f-122">如果您要與 Automation 或 COM 物件進行互動，請記住，某些型別的資料寬度會與在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中的資料寬度不同。</span><span class="sxs-lookup"><span data-stu-id="80a5f-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="80a5f-123">例如，`uint` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="80a5f-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="80a5f-124">如果您將 16 位元引數傳遞給這類元件，將它宣告為`UShort`而不是`UInteger`中受管理的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="80a5f-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80a5f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80a5f-125">See also</span></span>
- [<span data-ttu-id="80a5f-126">反映</span><span class="sxs-lookup"><span data-stu-id="80a5f-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)

