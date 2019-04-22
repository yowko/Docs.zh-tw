---
title: HOW TO：宣告物件變數，並在 Visual Basic 中將物件指派給它
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: fb6411efc190dce335422369a8d2bbff564b9523
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819667"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a><span data-ttu-id="ca335-102">HOW TO：宣告物件變數，並在 Visual Basic 中將物件指派給它</span><span class="sxs-lookup"><span data-stu-id="ca335-102">How to: Declare an Object Variable and Assign an Object to It in Visual Basic</span></span>
<span data-ttu-id="ca335-103">宣告的變數[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)藉由指定`As Object`中[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="ca335-103">You declare a variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) by specifying `As Object` in a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="ca335-104">將物件指派給這類變數的藉由將物件放在等號 (`=`) 在指派陳述式或初始化子句中。</span><span class="sxs-lookup"><span data-stu-id="ca335-104">You assign an object to such a variable by placing the object after the equal sign (`=`) in an assignment statement or initialization clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca335-105">範例</span><span class="sxs-lookup"><span data-stu-id="ca335-105">Example</span></span>  
 <span data-ttu-id="ca335-106">下列範例會宣告`Object`變數並指派給它的目前執行個體。</span><span class="sxs-lookup"><span data-stu-id="ca335-106">The following example declares an `Object` variable and assigns the current instance to it.</span></span>  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 <span data-ttu-id="ca335-107">您可以結合的宣告和指派變數初始化為其宣告的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca335-107">You can combine the declaration and assignment by initializing the variable as part of its declaration.</span></span> <span data-ttu-id="ca335-108">下列範例相當於上述的範例。</span><span class="sxs-lookup"><span data-stu-id="ca335-108">The following example is equivalent to the preceding example.</span></span>  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ca335-109">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ca335-109">Compiling the Code</span></span>  
 <span data-ttu-id="ca335-110">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ca335-110">This example requires:</span></span>  
  
-   <span data-ttu-id="ca335-111"><xref:System> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="ca335-111">A reference to the <xref:System> namespace.</span></span>  
  
-   <span data-ttu-id="ca335-112">類別、 結構或模組要放入`Dim`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ca335-112">A class, structure, or module in which to put the `Dim` statement.</span></span>  
  
-   <span data-ttu-id="ca335-113">中要放的指派陳述式的程序。</span><span class="sxs-lookup"><span data-stu-id="ca335-113">A procedure in which to put the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca335-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca335-114">See also</span></span>

- [<span data-ttu-id="ca335-115">變數宣告</span><span class="sxs-lookup"><span data-stu-id="ca335-115">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="ca335-116">物件變數</span><span class="sxs-lookup"><span data-stu-id="ca335-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ca335-117">物件變數宣告</span><span class="sxs-lookup"><span data-stu-id="ca335-117">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="ca335-118">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="ca335-118">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="ca335-119">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="ca335-119">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="ca335-120">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="ca335-120">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ca335-121">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="ca335-121">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
