---
title: 結構和其他程式設計項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819096"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a><span data-ttu-id="eb8f3-102">結構和其他程式設計項目 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb8f3-102">Structures and Other Programming Elements (Visual Basic)</span></span>
<span data-ttu-id="eb8f3-103">您可以使用結構搭配使用陣列、 物件和程序，以及彼此。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-103">You can use structures in conjunction with arrays, objects, and procedures, as well as with each other.</span></span> <span data-ttu-id="eb8f3-104">因為這些項目使用個別的互動會使用相同的語法。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-104">The interactions use the same syntax as these elements use individually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb8f3-105">您無法初始化任何在結構宣告中的結構項目。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-105">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="eb8f3-106">您只能指派值給變數已宣告為結構類型的項目。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-106">You can assign values only to elements of a variable that has been declared to be of a structure type.</span></span>  
  
## <a name="structures-and-arrays"></a><span data-ttu-id="eb8f3-107">結構和陣列</span><span class="sxs-lookup"><span data-stu-id="eb8f3-107">Structures and Arrays</span></span>  
 <span data-ttu-id="eb8f3-108">結構包含一個或多個子項目陣列。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-108">A structure can contain an array as one or more of its elements.</span></span> <span data-ttu-id="eb8f3-109">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-109">The following example illustrates this.</span></span>  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 <span data-ttu-id="eb8f3-110">存取陣列在結構中的值相同的方式存取物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-110">You access the values of an array within a structure the same way you access a property on an object.</span></span> <span data-ttu-id="eb8f3-111">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-111">The following example illustrates this.</span></span>  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 <span data-ttu-id="eb8f3-112">您也可以宣告結構的陣列。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-112">You can also declare an array of structures.</span></span> <span data-ttu-id="eb8f3-113">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-113">The following example illustrates this.</span></span>  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 <span data-ttu-id="eb8f3-114">您遵循相同的規則，來存取此資料架構的元件。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-114">You follow the same rules to access the components of this data architecture.</span></span> <span data-ttu-id="eb8f3-115">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-115">The following example illustrates this.</span></span>  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a><span data-ttu-id="eb8f3-116">結構和物件</span><span class="sxs-lookup"><span data-stu-id="eb8f3-116">Structures and Objects</span></span>  
 <span data-ttu-id="eb8f3-117">結構包含一個或多個子項目物件。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-117">A structure can contain an object as one or more of its elements.</span></span> <span data-ttu-id="eb8f3-118">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-118">The following example illustrates this.</span></span>  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 <span data-ttu-id="eb8f3-119">您應該使用特定的物件類別，在這類宣告中，而非`Object`。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-119">You should use a specific object class in such a declaration, rather than `Object`.</span></span>  
  
## <a name="structures-and-procedures"></a><span data-ttu-id="eb8f3-120">結構和程序</span><span class="sxs-lookup"><span data-stu-id="eb8f3-120">Structures and Procedures</span></span>  
 <span data-ttu-id="eb8f3-121">您可以傳遞結構做為程序引數。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-121">You can pass a structure as a procedure argument.</span></span> <span data-ttu-id="eb8f3-122">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-122">The following example illustrates this.</span></span>  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 <span data-ttu-id="eb8f3-123">上述範例中將結構傳遞*傳址*，可讓程序來修改其項目，讓呼叫端程式碼中所做的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-123">The preceding example passes the structure *by reference*, which allows the procedure to modify its elements so that the changes take effect in the calling code.</span></span> <span data-ttu-id="eb8f3-124">如果您想要保護對這類修改的結構，傳值方式傳遞。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-124">If you want to protect a structure against such modification, pass it by value.</span></span>  
  
 <span data-ttu-id="eb8f3-125">您也可以傳回結構，以從`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-125">You can also return a structure from a `Function` procedure.</span></span> <span data-ttu-id="eb8f3-126">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-126">The following example illustrates this.</span></span>  
  
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
  
## <a name="structures-within-structures"></a><span data-ttu-id="eb8f3-127">結構內的結構</span><span class="sxs-lookup"><span data-stu-id="eb8f3-127">Structures Within Structures</span></span>  
 <span data-ttu-id="eb8f3-128">結構可以包含其他結構。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-128">Structures can contain other structures.</span></span> <span data-ttu-id="eb8f3-129">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-129">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="eb8f3-130">您也可以使用這項技術來封裝在不同的模組中定義的結構內的其中一個模組中定義的結構。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-130">You can also use this technique to encapsulate a structure defined in one module within a structure defined in a different module.</span></span>  
  
 <span data-ttu-id="eb8f3-131">結構可以包含其他結構到任意深度。</span><span class="sxs-lookup"><span data-stu-id="eb8f3-131">Structures can contain other structures to an arbitrary depth.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8f3-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb8f3-132">See also</span></span>

- [<span data-ttu-id="eb8f3-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="eb8f3-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="eb8f3-134">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="eb8f3-134">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="eb8f3-135">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="eb8f3-135">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="eb8f3-136">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="eb8f3-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="eb8f3-137">結構</span><span class="sxs-lookup"><span data-stu-id="eb8f3-137">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="eb8f3-138">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="eb8f3-138">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="eb8f3-139">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="eb8f3-139">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="eb8f3-140">結構變數</span><span class="sxs-lookup"><span data-stu-id="eb8f3-140">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [<span data-ttu-id="eb8f3-141">結構和類別</span><span class="sxs-lookup"><span data-stu-id="eb8f3-141">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="eb8f3-142">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="eb8f3-142">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
