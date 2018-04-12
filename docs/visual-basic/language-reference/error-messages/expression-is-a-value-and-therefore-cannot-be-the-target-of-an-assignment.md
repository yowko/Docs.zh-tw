---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="2ac08-102">運算式是一個數值，不可以是指派的目標</span><span class="sxs-lookup"><span data-stu-id="2ac08-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="2ac08-103">陳述式嘗試將值指派給運算式。</span><span class="sxs-lookup"><span data-stu-id="2ac08-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="2ac08-104">您只能指派給值的可寫入變數、 屬性或陣列元素執行階段。</span><span class="sxs-lookup"><span data-stu-id="2ac08-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="2ac08-105">下列範例說明會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ac08-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="2ac08-106">類似的範例可以套用至屬性和陣列項目。</span><span class="sxs-lookup"><span data-stu-id="2ac08-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="2ac08-107">**間接存取。**</span><span class="sxs-lookup"><span data-stu-id="2ac08-107">**Indirect Access.**</span></span> <span data-ttu-id="2ac08-108">透過實值類型的間接存取也可以產生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ac08-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="2ac08-109">請考慮下列程式碼範例中，會嘗試設定的值<xref:System.Drawing.Point>藉由存取間接透過<xref:System.Windows.Forms.Control.Location%2A>。</span><span class="sxs-lookup"><span data-stu-id="2ac08-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="2ac08-110">前述範例中的最後一個陳述式會失敗，因為它會建立暫存配置的<xref:System.Drawing.Point>所傳回的結構<xref:System.Windows.Forms.Control.Location%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2ac08-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="2ac08-111">結構是實值類型，且陳述式執行後，不會保留暫時性結構。</span><span class="sxs-lookup"><span data-stu-id="2ac08-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="2ac08-112">藉由宣告和使用的變數未解決此問題<xref:System.Windows.Forms.Control.Location%2A>，這樣就可以建立更具永久性配置<xref:System.Drawing.Point>結構。</span><span class="sxs-lookup"><span data-stu-id="2ac08-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="2ac08-113">下列範例會顯示可以取代前述範例中的最後一個陳述式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2ac08-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="2ac08-114">**錯誤 ID:** BC30068</span><span class="sxs-lookup"><span data-stu-id="2ac08-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ac08-115">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2ac08-115">To correct this error</span></span>  
  
-   <span data-ttu-id="2ac08-116">如果陳述式指派值的運算式，運算式以取代單一可寫入的變數、 屬性或陣列元素。</span><span class="sxs-lookup"><span data-stu-id="2ac08-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="2ac08-117">如果此陳述式間接存取透過實值類型 （通常是結構），建立實值類型的變數。</span><span class="sxs-lookup"><span data-stu-id="2ac08-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="2ac08-118">將適當的結構 （或其他實值型別） 指派給變數。</span><span class="sxs-lookup"><span data-stu-id="2ac08-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="2ac08-119">您可以使用變數來存取要指派其值的屬性。</span><span class="sxs-lookup"><span data-stu-id="2ac08-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ac08-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ac08-120">See Also</span></span>  
 [<span data-ttu-id="2ac08-121">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="2ac08-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="2ac08-122">陳述式</span><span class="sxs-lookup"><span data-stu-id="2ac08-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="2ac08-123">程序的疑難排解</span><span class="sxs-lookup"><span data-stu-id="2ac08-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
