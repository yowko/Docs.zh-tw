---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: 3027be6ee4ed3664b81c661b6a086a3604573833
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826128"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="ed82b-102">運算式是一個數值，不可以是指派的目標</span><span class="sxs-lookup"><span data-stu-id="ed82b-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="ed82b-103">陳述式會嘗試將值指派給運算式。</span><span class="sxs-lookup"><span data-stu-id="ed82b-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="ed82b-104">您只能指派給可寫入的變數、 屬性或陣列元素的值，在執行階段。</span><span class="sxs-lookup"><span data-stu-id="ed82b-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="ed82b-105">下列範例說明如何可能會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed82b-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="ed82b-106">類似的範例可以套用至屬性和陣列項目。</span><span class="sxs-lookup"><span data-stu-id="ed82b-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="ed82b-107">**間接存取。**</span><span class="sxs-lookup"><span data-stu-id="ed82b-107">**Indirect Access.**</span></span> <span data-ttu-id="ed82b-108">透過實值類型的間接存取也可以產生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="ed82b-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="ed82b-109">下列程式碼範例，嘗試設定的值，請考慮<xref:System.Drawing.Point>藉由存取間接透過<xref:System.Windows.Forms.Control.Location%2A>。</span><span class="sxs-lookup"><span data-stu-id="ed82b-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="ed82b-110">前述範例中的最後一個陳述式會失敗，因為它會建立只有暫存的配置<xref:System.Drawing.Point>所傳回的結構<xref:System.Windows.Forms.Control.Location%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ed82b-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="ed82b-111">結構是實值類型，並執行陳述式之後，不會保留暫時性結構。</span><span class="sxs-lookup"><span data-stu-id="ed82b-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="ed82b-112">未解決此問題，藉由宣告和使用的變數<xref:System.Windows.Forms.Control.Location%2A>，以建立更永久的配置<xref:System.Drawing.Point>結構。</span><span class="sxs-lookup"><span data-stu-id="ed82b-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="ed82b-113">下列範例顯示可以取代前述範例中的最後一個陳述式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ed82b-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="ed82b-114">**錯誤 ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="ed82b-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ed82b-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ed82b-115">To correct this error</span></span>  
  
-   <span data-ttu-id="ed82b-116">如果陳述式會將值指派給運算式，運算式以取代單一可寫入的變數、 屬性或陣列元素。</span><span class="sxs-lookup"><span data-stu-id="ed82b-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="ed82b-117">如果此陳述式間接存取透過實值型別 （通常是結構），建立變數來保存實值型別。</span><span class="sxs-lookup"><span data-stu-id="ed82b-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="ed82b-118">將適當的結構 （或其他實值型別） 指派給變數。</span><span class="sxs-lookup"><span data-stu-id="ed82b-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="ed82b-119">您可以使用變數來存取屬性，以將它指派值。</span><span class="sxs-lookup"><span data-stu-id="ed82b-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed82b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed82b-120">See also</span></span>

- [<span data-ttu-id="ed82b-121">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="ed82b-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="ed82b-122">陳述式</span><span class="sxs-lookup"><span data-stu-id="ed82b-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="ed82b-123">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="ed82b-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
