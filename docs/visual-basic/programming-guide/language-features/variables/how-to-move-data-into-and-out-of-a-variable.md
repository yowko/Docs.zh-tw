---
title: 如何：移入和移出變數資料
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: fe19a6160623aa9ea867becdf7a15b51319abf45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410434"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="1e38c-102">如何：移入和移出變數資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e38c-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>

<span data-ttu-id="1e38c-103">您可以藉由將變數名稱放在指派語句的左邊，將值儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="1e38c-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>

## <a name="putting-data-in-a-variable"></a><span data-ttu-id="1e38c-104">將資料放入變數中</span><span class="sxs-lookup"><span data-stu-id="1e38c-104">Putting Data in a Variable</span></span>

#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="1e38c-105">將值儲存在變數中</span><span class="sxs-lookup"><span data-stu-id="1e38c-105">To store a value in a variable</span></span>

- <span data-ttu-id="1e38c-106">在指派語句的左邊使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="1e38c-106">Use the variable name on the left side of an assignment statement.</span></span>

    <span data-ttu-id="1e38c-107">下列範例會設定變數的值 `alpha` 。</span><span class="sxs-lookup"><span data-stu-id="1e38c-107">The following example sets the value of the variable `alpha`.</span></span>

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    <span data-ttu-id="1e38c-108">在指派語句的右邊產生的值會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="1e38c-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>

## <a name="getting-data-from-a-variable"></a><span data-ttu-id="1e38c-109">從變數取得資料</span><span class="sxs-lookup"><span data-stu-id="1e38c-109">Getting Data from a Variable</span></span>

<span data-ttu-id="1e38c-110">您可以藉由在運算式中包含變數名稱，來取出變數的值。</span><span class="sxs-lookup"><span data-stu-id="1e38c-110">You retrieve a variable's value by including the variable name in an expression.</span></span>

#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="1e38c-111">若要從變數中取出值</span><span class="sxs-lookup"><span data-stu-id="1e38c-111">To retrieve a value from a variable</span></span>

- <span data-ttu-id="1e38c-112">在運算式中使用變數名稱。</span><span class="sxs-lookup"><span data-stu-id="1e38c-112">Use the variable name in an expression.</span></span> <span data-ttu-id="1e38c-113">除了定義常數值的運算式以外，您可以在任何可使用常數或常值的地方使用變數。</span><span class="sxs-lookup"><span data-stu-id="1e38c-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>

  <span data-ttu-id="1e38c-114">\-或-</span><span class="sxs-lookup"><span data-stu-id="1e38c-114">\-or-</span></span>

- <span data-ttu-id="1e38c-115">在指派語句中的等號（）後面使用變數名稱 `=` 。</span><span class="sxs-lookup"><span data-stu-id="1e38c-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>

  <span data-ttu-id="1e38c-116">下列範例會讀取變數的值 `startValue` ，然後在運算式中使用變數的值 `counter` 。</span><span class="sxs-lookup"><span data-stu-id="1e38c-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  <span data-ttu-id="1e38c-117">變數的值會以常數的形式參與運算式，然後儲存在指派語句左側的變數或屬性中。</span><span class="sxs-lookup"><span data-stu-id="1e38c-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e38c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e38c-118">See also</span></span>

- [<span data-ttu-id="1e38c-119">變數</span><span class="sxs-lookup"><span data-stu-id="1e38c-119">Variables</span></span>](index.md)
- [<span data-ttu-id="1e38c-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="1e38c-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="1e38c-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="1e38c-121">Object Variables</span></span>](object-variables.md)
