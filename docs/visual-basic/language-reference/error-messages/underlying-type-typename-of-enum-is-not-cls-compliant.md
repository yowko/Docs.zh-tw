---
title: 列舉的基礎類型 <typename> 不符合 CLS 標準
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 42c2398945b97d68161af6fb3c3b69909f4aaf39
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161513"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="4620e-102">BC40032： \<typename> 列舉的基礎類型不符合 CLS 規範</span><span class="sxs-lookup"><span data-stu-id="4620e-102">BC40032: Underlying type \<typename> of Enum is not CLS-compliant</span></span>

<span data-ttu-id="4620e-103">針對此列舉指定的資料類型不是 [語言獨立性的一部分，而](../../../standard/language-independence-and-language-independent-components.md) 是 (CLS) 的 Language-Independent 元件。</span><span class="sxs-lookup"><span data-stu-id="4620e-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="4620e-104">這不是您的元件內的錯誤，因為 .NET Framework 和 Visual Basic 支援此資料類型。</span><span class="sxs-lookup"><span data-stu-id="4620e-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="4620e-105">不過，以嚴格符合 CLS 標準的程式碼撰寫的另一個元件可能不支援此資料類型。</span><span class="sxs-lookup"><span data-stu-id="4620e-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="4620e-106">這類元件可能無法成功與您的元件互動。</span><span class="sxs-lookup"><span data-stu-id="4620e-106">Such a component might not be able to interact successfully with your component.</span></span>

 <span data-ttu-id="4620e-107">下列 Visual Basic 資料類型不符合 CLS 規範：</span><span class="sxs-lookup"><span data-stu-id="4620e-107">The following Visual Basic data types are not CLS-compliant:</span></span>

- [<span data-ttu-id="4620e-108">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="4620e-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)

- [<span data-ttu-id="4620e-109">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="4620e-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)

- [<span data-ttu-id="4620e-110">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="4620e-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)

- [<span data-ttu-id="4620e-111">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="4620e-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)

 <span data-ttu-id="4620e-112">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="4620e-112">By default, this message is a warning.</span></span> <span data-ttu-id="4620e-113">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="4620e-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="4620e-114">**錯誤識別碼：** BC40032</span><span class="sxs-lookup"><span data-stu-id="4620e-114">**Error ID:** BC40032</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4620e-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4620e-115">To correct this error</span></span>

- <span data-ttu-id="4620e-116">如果您的元件僅與其他 .NET Framework 元件互動，或未與任何其他元件互動，您就不需要變更任何動作。</span><span class="sxs-lookup"><span data-stu-id="4620e-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>

- <span data-ttu-id="4620e-117">如果您要與未針對 .NET Framework 撰寫的元件進行互動，您可以透過反映或從檔中判斷是否支援此資料類型。</span><span class="sxs-lookup"><span data-stu-id="4620e-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="4620e-118">如果有，您就不需要變更任何變更。</span><span class="sxs-lookup"><span data-stu-id="4620e-118">If it does, you do not need to change anything.</span></span>

- <span data-ttu-id="4620e-119">如果您要與不支援此資料類型的元件互動，您必須將它取代為最符合 CLS 標準的類型。</span><span class="sxs-lookup"><span data-stu-id="4620e-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="4620e-120">例如，如果您不需要 2,147,483,647 以上的值範圍，而且不使用 `UInteger` ，則可能可以使用 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="4620e-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="4620e-121">如果您需要擴充範圍，則可以將 `UInteger` 取代為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="4620e-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>

- <span data-ttu-id="4620e-122">如果您要與 Automation 或 COM 物件互動，請記住，有些類型的資料寬度會與 .NET Framework 中的資料寬度不同。</span><span class="sxs-lookup"><span data-stu-id="4620e-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="4620e-123">例如，`uint` 在其他環境中通常是 16 位元。</span><span class="sxs-lookup"><span data-stu-id="4620e-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="4620e-124">如果您要將16位引數傳遞至這類元件，請 `UShort` `UInteger` 在您的 managed Visual Basic 程式碼中將它宣告為，而不是。</span><span class="sxs-lookup"><span data-stu-id="4620e-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

## <a name="see-also"></a><span data-ttu-id="4620e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4620e-125">See also</span></span>

- [<span data-ttu-id="4620e-126">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4620e-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="4620e-127">反射</span><span class="sxs-lookup"><span data-stu-id="4620e-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
