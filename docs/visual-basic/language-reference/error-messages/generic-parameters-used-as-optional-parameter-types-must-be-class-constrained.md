---
title: 用來做為選擇性參數類型的泛型參數必須受到類別條件約束
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 5e0d4eaf7557eb9a544a8845299f3d69dbb78486
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163216"
---
# <a name="bc32124-generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a><span data-ttu-id="533d6-102">BC32124：用來當做選擇性參數類型的泛型參數必須是類別條件約束</span><span class="sxs-lookup"><span data-stu-id="533d6-102">BC32124: Generic parameters used as optional parameter types must be class constrained</span></span>

<span data-ttu-id="533d6-103">使用選擇性參數宣告程式，此參數使用的類型參數不受限於參考型別。</span><span class="sxs-lookup"><span data-stu-id="533d6-103">A procedure is declared with an optional parameter that uses a type parameter that is not constrained to be a reference type.</span></span>

 <span data-ttu-id="533d6-104">您必須一律為每個選擇性參數提供預設值。</span><span class="sxs-lookup"><span data-stu-id="533d6-104">You must always supply a default value for each optional parameter.</span></span> <span data-ttu-id="533d6-105">如果參數是參考型別，則選擇性的值必須是 `Nothing` ，也就是任何參考型別的有效值。</span><span class="sxs-lookup"><span data-stu-id="533d6-105">If the parameter is of a reference type, the optional value must be `Nothing`, which is a valid value for any reference type.</span></span> <span data-ttu-id="533d6-106">但是，如果參數是實值型別，則該型別必須是 Visual Basic 預先定義的基本資料型別。</span><span class="sxs-lookup"><span data-stu-id="533d6-106">However, if the parameter is of a value type, that type must be an elementary data type predefined by Visual Basic.</span></span> <span data-ttu-id="533d6-107">這是因為複合實值型別（例如使用者定義的結構）沒有有效的預設值。</span><span class="sxs-lookup"><span data-stu-id="533d6-107">This is because a composite value type, such as a user-defined structure, has no valid default value.</span></span>

 <span data-ttu-id="533d6-108">當您針對選擇性參數使用型別參數時，必須保證它是參考型別，以避免實值型別的可能沒有有效的預設值。</span><span class="sxs-lookup"><span data-stu-id="533d6-108">When you use a type parameter for an optional parameter, you must guarantee that it is of a reference type to avoid the possibility of a value type with no valid default value.</span></span> <span data-ttu-id="533d6-109">這表示您必須使用 `Class` 關鍵字或特定類別的名稱來限制類型參數。</span><span class="sxs-lookup"><span data-stu-id="533d6-109">This means you must constrain the type parameter either with the `Class` keyword or with the name of a specific class.</span></span>

 <span data-ttu-id="533d6-110">**錯誤識別碼：** BC32124</span><span class="sxs-lookup"><span data-stu-id="533d6-110">**Error ID:** BC32124</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="533d6-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="533d6-111">To correct this error</span></span>

- <span data-ttu-id="533d6-112">將型別參數限制為只接受參考型別，或不要將它用於選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="533d6-112">Constrain the type parameter to accept only a reference type, or do not use it for the optional parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="533d6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="533d6-113">See also</span></span>

- [<span data-ttu-id="533d6-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="533d6-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="533d6-115">Type List</span><span class="sxs-lookup"><span data-stu-id="533d6-115">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="533d6-116">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="533d6-116">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="533d6-117">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="533d6-117">Optional Parameters</span></span>](../../programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="533d6-118">結構</span><span class="sxs-lookup"><span data-stu-id="533d6-118">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="533d6-119">什麼</span><span class="sxs-lookup"><span data-stu-id="533d6-119">Nothing</span></span>](../nothing.md)
