---
title: 在將 'ByRef' 參數 '<typename1>' 的值複製回相對應的引數時，將 '<typename2>' 隱含轉換至 '<parametername>'
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: a95a4b792742efcc165f7c7a9592582d34618f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162800"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="8eda5-102">BC41999： \<typename1> 將 \<typename2> ' ByRef ' 參數 ' ' 的值複製 \<parametername> 回相符的引數時，從 ' ' 隱含轉換成 ' '。</span><span class="sxs-lookup"><span data-stu-id="8eda5-102">BC41999: Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>

<span data-ttu-id="8eda5-103">使用與其對應參數不同類型的 [ByRef](../modifiers/byref.md) 引數來呼叫程式。</span><span class="sxs-lookup"><span data-stu-id="8eda5-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>

 <span data-ttu-id="8eda5-104">如果您傳遞引數 `ByRef` ，Visual Basic 有時會將引數值複製至程式中的區域變數，而不是傳遞參考。</span><span class="sxs-lookup"><span data-stu-id="8eda5-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="8eda5-105">在這種情況下，當程式傳回時，Visual Basic 必須接著將區域變數值複製回呼叫程式碼中的引數。</span><span class="sxs-lookup"><span data-stu-id="8eda5-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="8eda5-106">如果將 `ByRef` 引數值複製至程序，而且引數和參數的類型相同，則不需要進行轉換。</span><span class="sxs-lookup"><span data-stu-id="8eda5-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="8eda5-107">但是，如果類型不同，Visual Basic 必須雙向轉換。</span><span class="sxs-lookup"><span data-stu-id="8eda5-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="8eda5-108">因為您無法 `CType` 在程式引數或參數上使用或其他任何轉換關鍵字，所以這類轉換一律是隱含的。</span><span class="sxs-lookup"><span data-stu-id="8eda5-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>

 <span data-ttu-id="8eda5-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="8eda5-109">By default, this message is a warning.</span></span> <span data-ttu-id="8eda5-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="8eda5-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="8eda5-111">**錯誤識別碼：** BC41999</span><span class="sxs-lookup"><span data-stu-id="8eda5-111">**Error ID:** BC41999</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8eda5-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8eda5-112">To correct this error</span></span>

- <span data-ttu-id="8eda5-113">可能的話，請使用與程式參數相同類型的呼叫引數，因此 Visual Basic 不需要進行任何轉換。</span><span class="sxs-lookup"><span data-stu-id="8eda5-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="8eda5-114">如果您需要呼叫引數類型與參數類型不同的程序，但不需要將值傳回給呼叫中引數，請將此參數定義為 [ByVal](../modifiers/byval.md) ，而非 `ByRef`。</span><span class="sxs-lookup"><span data-stu-id="8eda5-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

## <a name="see-also"></a><span data-ttu-id="8eda5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eda5-115">See also</span></span>

- [<span data-ttu-id="8eda5-116">程序</span><span class="sxs-lookup"><span data-stu-id="8eda5-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="8eda5-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="8eda5-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8eda5-118">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="8eda5-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="8eda5-119">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="8eda5-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
