---
title: 作法：在 Visual Basic 中, 宣告物件變數並指派物件給它
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 71949d50b01d7f252a988e86ca259261086d3b3b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630880"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="4bbff-102">作法：在 Visual Basic 中, 宣告物件變數並指派物件給它</span><span class="sxs-lookup"><span data-stu-id="4bbff-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>

<span data-ttu-id="4bbff-103">您可以在[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)中指定`As Object` , 以宣告[Object 資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)的變數。</span><span class="sxs-lookup"><span data-stu-id="4bbff-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="4bbff-104">將物件放在指派語句或初始化子句中的等號 (`=`) 後面, 即可將物件指派給這類變數。</span><span class="sxs-lookup"><span data-stu-id="4bbff-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>

## <a name="example"></a><span data-ttu-id="4bbff-105">範例</span><span class="sxs-lookup"><span data-stu-id="4bbff-105">Example</span></span>

<span data-ttu-id="4bbff-106">下列範例會宣告一個`Object`變數, 並將目前的實例指派給它。</span><span class="sxs-lookup"><span data-stu-id="4bbff-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

<span data-ttu-id="4bbff-107">您可以將變數初始化為其宣告的一部分, 藉此結合宣告和指派。</span><span class="sxs-lookup"><span data-stu-id="4bbff-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="4bbff-108">下列範例相當於上述範例。</span><span class="sxs-lookup"><span data-stu-id="4bbff-108">The following example is equivalent to the preceding example.</span></span>

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compiling-the-code"></a><span data-ttu-id="4bbff-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="4bbff-109">Compiling the Code</span></span>

<span data-ttu-id="4bbff-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="4bbff-110">This example requires:</span></span>

- <span data-ttu-id="4bbff-111">          <xref:System> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="4bbff-111">A reference to the <xref:System> namespace.</span></span>

- <span data-ttu-id="4bbff-112">要在其中放置`Dim`語句的類別、結構或模組。</span><span class="sxs-lookup"><span data-stu-id="4bbff-112">A class, structure, or module in which to put the `Dim` statement.</span></span>

- <span data-ttu-id="4bbff-113">要在其中放置指派語句的程式。</span><span class="sxs-lookup"><span data-stu-id="4bbff-113">A procedure in which to put the assignment statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bbff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bbff-114">See also</span></span>

- [<span data-ttu-id="4bbff-115">變數宣告</span><span class="sxs-lookup"><span data-stu-id="4bbff-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="4bbff-116">物件變數</span><span class="sxs-lookup"><span data-stu-id="4bbff-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="4bbff-117">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="4bbff-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="4bbff-118">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="4bbff-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="4bbff-119">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="4bbff-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="4bbff-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="4bbff-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="4bbff-121">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="4bbff-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
