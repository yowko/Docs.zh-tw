---
title: 無法從委派推斷型別引數
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 3e2902da7fe9d8fa2194db681df098f0148cbbaf
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584252"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a><span data-ttu-id="490d7-102">無法從委派推斷型別引數</span><span class="sxs-lookup"><span data-stu-id="490d7-102">Type arguments could not be inferred from the delegate</span></span>
<span data-ttu-id="490d7-103">指派陳述式使用 `AddressOf` 將泛型程序的位址指派給委派，但未將任何類型引數提供給泛型程序。</span><span class="sxs-lookup"><span data-stu-id="490d7-103">An assignment statement uses `AddressOf` to assign the address of a generic procedure to a delegate, but it does not supply any type arguments to the generic procedure.</span></span>  
  
 <span data-ttu-id="490d7-104">通常，當您叫用泛型類型時，會針對泛型類型所定義的每個類型參數提供類型引數。</span><span class="sxs-lookup"><span data-stu-id="490d7-104">Normally, when you invoke a generic type, you supply a type argument for each type parameter that the generic type defines.</span></span> <span data-ttu-id="490d7-105">如果您未提供任何類型引數，編譯器會嘗試推斷要傳遞給類型參數的類型。</span><span class="sxs-lookup"><span data-stu-id="490d7-105">If you do not supply any type arguments, the compiler attempts to infer the types to be passed to the type parameters.</span></span> <span data-ttu-id="490d7-106">如果內容未提供足夠的資訊讓編譯器推斷類型，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="490d7-106">If the context does not provide enough information for the compiler to infer the types, an error is generated.</span></span>  
  
 <span data-ttu-id="490d7-107">**錯誤 ID:** BC36564</span><span class="sxs-lookup"><span data-stu-id="490d7-107">**Error ID:** BC36564</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="490d7-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="490d7-108">To correct this error</span></span>  
  
- <span data-ttu-id="490d7-109">在 `AddressOf` 運算式中指定泛型程序的類型引數。</span><span class="sxs-lookup"><span data-stu-id="490d7-109">Specify the type arguments for the generic procedure in the `AddressOf` expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490d7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="490d7-110">See also</span></span>

- [<span data-ttu-id="490d7-111">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="490d7-111">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="490d7-112">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="490d7-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="490d7-113">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="490d7-113">Generic Procedures in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="490d7-114">類型清單</span><span class="sxs-lookup"><span data-stu-id="490d7-114">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="490d7-115">擴充方法</span><span class="sxs-lookup"><span data-stu-id="490d7-115">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
