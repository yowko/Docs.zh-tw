---
title: 結構變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663384"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="37c4a-102">結構變數 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37c4a-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="37c4a-103">當您建立結構之後時，您可以為該型別來宣告程序層級和模組層級變數。</span><span class="sxs-lookup"><span data-stu-id="37c4a-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="37c4a-104">例如，您可以建立結構的電腦系統的相關記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="37c4a-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="37c4a-105">下列範例為其示範。</span><span class="sxs-lookup"><span data-stu-id="37c4a-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="37c4a-106">您現在可以宣告該類型的變數。</span><span class="sxs-lookup"><span data-stu-id="37c4a-106">You can now declare variables of that type.</span></span> <span data-ttu-id="37c4a-107">下列宣告將說明這點。</span><span class="sxs-lookup"><span data-stu-id="37c4a-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="37c4a-108">在類別和模組中，使用宣告的結構[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)預設為公用存取。</span><span class="sxs-lookup"><span data-stu-id="37c4a-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="37c4a-109">如果您想要為私用的結構，請確定您使用宣告[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="37c4a-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="37c4a-110">結構值的存取權</span><span class="sxs-lookup"><span data-stu-id="37c4a-110">Access to Structure Values</span></span>  
 <span data-ttu-id="37c4a-111">若要指派及擷取結構變數的項目中的值，您會使用相同的語法，如同您使用來設定和取得屬性的物件上。</span><span class="sxs-lookup"><span data-stu-id="37c4a-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="37c4a-112">您將成員存取運算子 (`.`) 結構的變數名稱之間的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="37c4a-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="37c4a-113">下列範例會存取變數先前宣告為類型的項目`systemInfo`。</span><span class="sxs-lookup"><span data-stu-id="37c4a-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="37c4a-114">指派結構變數</span><span class="sxs-lookup"><span data-stu-id="37c4a-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="37c4a-115">您也可以指派到另一個變數，如果兩個都是相同的結構類型。</span><span class="sxs-lookup"><span data-stu-id="37c4a-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="37c4a-116">這會將一個結構的所有項目複製到其他的對應項目。</span><span class="sxs-lookup"><span data-stu-id="37c4a-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="37c4a-117">下列宣告將說明這點。</span><span class="sxs-lookup"><span data-stu-id="37c4a-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="37c4a-118">如果結構項目是參考類型，如`String`， `Object`，或複製的資料指標的陣列。</span><span class="sxs-lookup"><span data-stu-id="37c4a-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="37c4a-119">在上述範例中，如果`systemInfo`已包含物件變數，則會將上述範例中會複製從指標`mySystem`到`yourSystem`，並透過一個結構物件的資料變更會是作用中時存取透過其他的結構。</span><span class="sxs-lookup"><span data-stu-id="37c4a-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c4a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37c4a-120">See also</span></span>

- [<span data-ttu-id="37c4a-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="37c4a-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="37c4a-122">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="37c4a-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="37c4a-123">複合資料類型</span><span class="sxs-lookup"><span data-stu-id="37c4a-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="37c4a-124">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="37c4a-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="37c4a-125">結構</span><span class="sxs-lookup"><span data-stu-id="37c4a-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="37c4a-126">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="37c4a-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="37c4a-127">如何：宣告結構</span><span class="sxs-lookup"><span data-stu-id="37c4a-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="37c4a-128">結構和其他程式設計項目</span><span class="sxs-lookup"><span data-stu-id="37c4a-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="37c4a-129">結構和類別</span><span class="sxs-lookup"><span data-stu-id="37c4a-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="37c4a-130">Structure 陳述式</span><span class="sxs-lookup"><span data-stu-id="37c4a-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
