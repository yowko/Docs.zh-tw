---
title: 成員 '<membername>' 的類型不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords:
- BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
ms.openlocfilehash: f6f66617774dccff4450cce42904126acf5c3769
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590681"
---
# <a name="type-of-member-membername-is-not-cls-compliant"></a><span data-ttu-id="f12e5-102">成員的型別 '\<成員名稱 >' 不符合 CLS 標準</span><span class="sxs-lookup"><span data-stu-id="f12e5-102">Type of member '\<membername>' is not CLS-compliant</span></span>
<span data-ttu-id="f12e5-103">指定不是這個成員的資料類型的一部分[Language Independence and Language-independent Components](../../../standard/language-independence-and-language-independent-components.md) （cls） 標準。</span><span class="sxs-lookup"><span data-stu-id="f12e5-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="f12e5-104">因為.NET Framework 和 Visual Basic 支援這種資料類型，這是不在您的元件中發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f12e5-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="f12e5-105">不過，另一個以完全符合 CLS 標準的程式碼撰寫的元件可能不支援這種資料類型。</span><span class="sxs-lookup"><span data-stu-id="f12e5-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="f12e5-106">這類元件可能無法順利與您的元件互動。</span><span class="sxs-lookup"><span data-stu-id="f12e5-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="f12e5-107">下列 Visual Basic 資料類型不符合 CLS 標準：</span><span class="sxs-lookup"><span data-stu-id="f12e5-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="f12e5-108">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="f12e5-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="f12e5-109">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="f12e5-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="f12e5-110">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="f12e5-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="f12e5-111">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="f12e5-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="f12e5-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="f12e5-112">By default, this message is a warning.</span></span> <span data-ttu-id="f12e5-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="f12e5-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f12e5-114">**錯誤 ID:** BC40025</span><span class="sxs-lookup"><span data-stu-id="f12e5-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f12e5-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f12e5-115">To correct this error</span></span>  
  
- <span data-ttu-id="f12e5-116">如果您的元件只能與其他.NET Framework 元件、 介面或不會與其他任何元件介面，則您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="f12e5-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="f12e5-117">如果您要使用的不是針對.NET Framework 撰寫的元件，您可能無法透過反映或文件，判斷是否支援此資料型別。</span><span class="sxs-lookup"><span data-stu-id="f12e5-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="f12e5-118">若是如此，您不需要變更任何項目。</span><span class="sxs-lookup"><span data-stu-id="f12e5-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="f12e5-119">如果您要使用的元件不支援這種資料類型，您必須將它取代最符合 CLS 規範的型別。</span><span class="sxs-lookup"><span data-stu-id="f12e5-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="f12e5-120">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f12e5-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="f12e5-121">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="f12e5-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="f12e5-122">如果您要使用的 Automation 或 COM 物件，請記住，某些類型會有不同的資料寬度比在.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="f12e5-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="f12e5-123">例如，`uint` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="f12e5-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="f12e5-124">如果您將 16 位元引數傳遞給這類元件，將它宣告為`UShort`而不是`UInteger`中受管理的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f12e5-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12e5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f12e5-125">See also</span></span>

- [<span data-ttu-id="f12e5-126">反映</span><span class="sxs-lookup"><span data-stu-id="f12e5-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
