---
title: 用來做為選擇性參數類型的泛型參數必須受到類別條件約束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 9b0293472f5eda74c2bf8fb215e15ae5cf8d8b98
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813895"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="9f083-102">用來做為選擇性參數類型的泛型參數必須受到類別條件約束</span><span class="sxs-lookup"><span data-stu-id="9f083-102">Generic parameters used as optional parameter types must be class constrained</span></span>
<span data-ttu-id="9f083-103">程序會宣告使用不受限制是參考類型的型別參數的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="9f083-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>  
  
 <span data-ttu-id="9f083-104">您一律必須提供每個選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="9f083-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="9f083-105">如果參數是參考型別，選擇性的值必須是`Nothing`，這是任何參考型別的有效的值。</span><span class="sxs-lookup"><span data-stu-id="9f083-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="9f083-106">不過，如果參數是實值類型，該類型必須是基本資料類型預先定義的 Visual basic。</span><span class="sxs-lookup"><span data-stu-id="9f083-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="9f083-107">這是因為複合值類型，例如使用者定義的結構，沒有任何有效的預設值。</span><span class="sxs-lookup"><span data-stu-id="9f083-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>  
  
 <span data-ttu-id="9f083-108">當您使用的型別參數為選擇性的參數時，您必須保證它是為了避免沒有有效的預設值的實值類型為參考型別。</span><span class="sxs-lookup"><span data-stu-id="9f083-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="9f083-109">這表示您必須使用限制的型別參數`Class`關鍵字或特定類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="9f083-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>  
  
 <span data-ttu-id="9f083-110">**錯誤 ID:** BC32124</span><span class="sxs-lookup"><span data-stu-id="9f083-110">**Error ID:** BC32124</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f083-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9f083-111">To correct this error</span></span>  
  
-   <span data-ttu-id="9f083-112">限制類型參數接受僅參考型別，或請勿使用它在選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="9f083-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f083-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f083-113">See also</span></span>

- [<span data-ttu-id="9f083-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f083-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="9f083-115">類型清單</span><span class="sxs-lookup"><span data-stu-id="9f083-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="9f083-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="9f083-116">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="9f083-117">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="9f083-117">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="9f083-118">結構</span><span class="sxs-lookup"><span data-stu-id="9f083-118">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="9f083-119">Nothing</span><span class="sxs-lookup"><span data-stu-id="9f083-119">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)
