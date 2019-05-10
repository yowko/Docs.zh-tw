---
title: HOW TO：將資料移入和移出變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 033d1cb0116b78ca9e3677c920ee5745117573d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663522"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a><span data-ttu-id="51c8d-102">HOW TO：將資料移入和移出變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51c8d-102">How to: Move Data Into and Out of a Variable (Visual Basic)</span></span>
<span data-ttu-id="51c8d-103">您將變數的名稱放在指派陳述式左邊值儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="51c8d-103">You store a value in a variable by putting the variable name on the left side of an assignment statement.</span></span>  
  
## <a name="putting-data-in-a-variable"></a><span data-ttu-id="51c8d-104">將資料放在變數中</span><span class="sxs-lookup"><span data-stu-id="51c8d-104">Putting Data in a Variable</span></span>  
  
#### <a name="to-store-a-value-in-a-variable"></a><span data-ttu-id="51c8d-105">若要儲存在變數中的值</span><span class="sxs-lookup"><span data-stu-id="51c8d-105">To store a value in a variable</span></span>  
  
- <span data-ttu-id="51c8d-106">在指派陳述式左邊使用的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="51c8d-106">Use the variable name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="51c8d-107">下列範例會設定變數的值`alpha`。</span><span class="sxs-lookup"><span data-stu-id="51c8d-107">The following example sets the value of the variable `alpha`.</span></span>  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     <span data-ttu-id="51c8d-108">指派陳述式右側所產生的值會儲存在變數中。</span><span class="sxs-lookup"><span data-stu-id="51c8d-108">The value generated on the right side of the assignment statement is stored in the variable.</span></span>  
  
## <a name="getting-data-from-a-variable"></a><span data-ttu-id="51c8d-109">從變數取得資料</span><span class="sxs-lookup"><span data-stu-id="51c8d-109">Getting Data from a Variable</span></span>  
 <span data-ttu-id="51c8d-110">您可以在運算式中包括變數的名稱擷取變數的值。</span><span class="sxs-lookup"><span data-stu-id="51c8d-110">You retrieve a variable's value by including the variable name in an expression.</span></span>  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a><span data-ttu-id="51c8d-111">從變數擷取值</span><span class="sxs-lookup"><span data-stu-id="51c8d-111">To retrieve a value from a variable</span></span>  
  
- <span data-ttu-id="51c8d-112">在運算式中使用變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="51c8d-112">Use the variable name in an expression.</span></span> <span data-ttu-id="51c8d-113">您可以使用變數任何地方您可以使用常數或常值，除了中定義的常數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="51c8d-113">You can use a variable anywhere you can use a constant or a literal, except in an expression that defines the value of a constant.</span></span>  
  
     <span data-ttu-id="51c8d-114">-或-</span><span class="sxs-lookup"><span data-stu-id="51c8d-114">-or-</span></span>  
  
- <span data-ttu-id="51c8d-115">使用下列相等的變數名稱 (`=`) 登入在指派陳述式。</span><span class="sxs-lookup"><span data-stu-id="51c8d-115">Use the variable name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="51c8d-116">下列範例會讀取變數的值`startValue`，然後使用變數的值`counter`在運算式中。</span><span class="sxs-lookup"><span data-stu-id="51c8d-116">The following example reads the value of the variable `startValue` and then uses the value of the variable `counter` in an expression.</span></span>  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     <span data-ttu-id="51c8d-117">變數的值會參與運算式，就如同常數會，並再儲存在變數或指派陳述式左邊的屬性。</span><span class="sxs-lookup"><span data-stu-id="51c8d-117">The value of the variable participates in the expression just as a constant would, and then it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c8d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51c8d-118">See also</span></span>

- [<span data-ttu-id="51c8d-119">變數</span><span class="sxs-lookup"><span data-stu-id="51c8d-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="51c8d-120">變數宣告</span><span class="sxs-lookup"><span data-stu-id="51c8d-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="51c8d-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="51c8d-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
