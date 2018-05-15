---
title: 如何：在 Visual Basic 中宣告物件變數，並指派物件給它
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: 1f38c90f0571b3fc73c4c89812092cdada936d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="e8a3d-102">如何：在 Visual Basic 中宣告物件變數，並指派物件給它</span><span class="sxs-lookup"><span data-stu-id="e8a3d-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="e8a3d-103">宣告的變數[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)藉由指定`As Object`中[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="e8a3d-104">將物件指派給這類變數的物件放在等號後面 (`=`) 在指派陳述式或初始化子句中。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8a3d-105">範例</span><span class="sxs-lookup"><span data-stu-id="e8a3d-105">Example</span></span>  
 <span data-ttu-id="e8a3d-106">下列範例會宣告`Object`變數並指派給它的目前執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="e8a3d-107">您可以結合的宣告和指派變數初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="e8a3d-108">下列範例就相當於上述範例。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8a3d-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e8a3d-109">Compiling the Code</span></span>  
 <span data-ttu-id="e8a3d-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e8a3d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e8a3d-111"><xref:System> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="e8a3d-112">類別、 結構或模組中，要放置`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="e8a3d-113">中要放置指派陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="e8a3d-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8a3d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8a3d-114">See Also</span></span>  
 [<span data-ttu-id="e8a3d-115">變數宣告</span><span class="sxs-lookup"><span data-stu-id="e8a3d-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="e8a3d-116">物件變數</span><span class="sxs-lookup"><span data-stu-id="e8a3d-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="e8a3d-117">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="e8a3d-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="e8a3d-118">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="e8a3d-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="e8a3d-119">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="e8a3d-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="e8a3d-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="e8a3d-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="e8a3d-121">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="e8a3d-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
