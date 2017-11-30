---
title: "結構和其他程式設計項目 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de343c06ec255d6cb68aa25d733e85385e884769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="ab221-102">結構和其他程式設計項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab221-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="ab221-103">您可以使用結構搭配陣列、 物件和程序，以及彼此搭配。</span><span class="sxs-lookup"><span data-stu-id="ab221-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="ab221-104">互動使用這些項目個別使用相同的語法。</span><span class="sxs-lookup"><span data-stu-id="ab221-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab221-105">您無法初始化任何結構中的項目結構宣告。</span><span class="sxs-lookup"><span data-stu-id="ab221-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="ab221-106">您只能指派給值的變數已宣告為結構類型的項目。</span><span class="sxs-lookup"><span data-stu-id="ab221-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="ab221-107">結構和陣列</span><span class="sxs-lookup"><span data-stu-id="ab221-107">Structures and Arrays</span></span>  
 <span data-ttu-id="ab221-108">結構只能包含一個或多個元素的陣列。</span><span class="sxs-lookup"><span data-stu-id="ab221-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="ab221-109">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="ab221-110">存取陣列在結構中的值相同的方式存取物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="ab221-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="ab221-111">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="ab221-112">您也可以宣告結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="ab221-112">You can also declare an array of structures.</span></span> <span data-ttu-id="ab221-113">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="ab221-114">您遵循相同的規則，來存取此資料架構的元件。</span><span class="sxs-lookup"><span data-stu-id="ab221-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="ab221-115">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="ab221-116">結構和物件</span><span class="sxs-lookup"><span data-stu-id="ab221-116">Structures and Objects</span></span>  
 <span data-ttu-id="ab221-117">結構只能包含一個或多個元素的物件。</span><span class="sxs-lookup"><span data-stu-id="ab221-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="ab221-118">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="ab221-119">您應該使用特定的物件類別中宣告，而非`Object`。</span><span class="sxs-lookup"><span data-stu-id="ab221-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="ab221-120">結構和程序</span><span class="sxs-lookup"><span data-stu-id="ab221-120">Structures and Procedures</span></span>  
 <span data-ttu-id="ab221-121">您可以傳遞結構做為程序引數。</span><span class="sxs-lookup"><span data-stu-id="ab221-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="ab221-122">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="ab221-123">上述範例中將結構傳遞*傳*，可讓程序來修改其項目，讓呼叫的程式碼中所做的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="ab221-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="ab221-124">如果您想要保護進行這類修改的結構，傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="ab221-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="ab221-125">您也可以傳回的結構從`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="ab221-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="ab221-126">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-126">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a><span data-ttu-id="ab221-127">在結構內的結構</span><span class="sxs-lookup"><span data-stu-id="ab221-127">Structures Within Structures</span></span>  
 <span data-ttu-id="ab221-128">結構可以包含其他結構。</span><span class="sxs-lookup"><span data-stu-id="ab221-128">Structures can contain other structures.</span></span> <span data-ttu-id="ab221-129">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="ab221-129">The following example illustrates this.</span></span>  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 <span data-ttu-id="ab221-130">您也可以使用這項技術來封裝在模組內的不同模組中定義的結構中定義的結構。</span><span class="sxs-lookup"><span data-stu-id="ab221-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="ab221-131">結構可以包含到任意深度的其他結構。</span><span class="sxs-lookup"><span data-stu-id="ab221-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab221-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab221-132">See Also</span></span>  
 [<span data-ttu-id="ab221-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="ab221-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="ab221-134">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="ab221-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="ab221-135">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="ab221-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="ab221-136">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="ab221-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="ab221-137">結構</span><span class="sxs-lookup"><span data-stu-id="ab221-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="ab221-138">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="ab221-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ab221-139">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="ab221-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="ab221-140">結構變數</span><span class="sxs-lookup"><span data-stu-id="ab221-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="ab221-141">結構和類別</span><span class="sxs-lookup"><span data-stu-id="ab221-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="ab221-142">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab221-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
