---
title: HOW TO：決定物件變數參考 (Visual Basic) 的類型
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 6499dfce880cc9ce16e5d77887afc0598692f48e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342865"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="1dd72-102">HOW TO：決定物件變數參考 (Visual Basic) 的類型</span><span class="sxs-lookup"><span data-stu-id="1dd72-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="1dd72-103">物件變數包含儲存在其他地方的資料指標。</span><span class="sxs-lookup"><span data-stu-id="1dd72-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="1dd72-104">在執行階段，可以變更該資料型別。</span><span class="sxs-lookup"><span data-stu-id="1dd72-104">The type of that data can change during run time.</span></span> <span data-ttu-id="1dd72-105">在任何時刻，您可以使用<xref:System.Type.GetTypeCode%2A>方法，以判斷目前的執行階段類型，或有[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來找出是否有目前的執行階段類型是與指定的型別相容。</span><span class="sxs-lookup"><span data-stu-id="1dd72-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="1dd72-106">若要判斷的確切型別物件變數目前參考</span><span class="sxs-lookup"><span data-stu-id="1dd72-106">To determine the exact type an object variable currently refers to</span></span>  
  
1. <span data-ttu-id="1dd72-107">物件變數上呼叫<xref:System.Object.GetType%2A>方法來擷取<xref:System.Type?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="1dd72-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2. <span data-ttu-id="1dd72-108">在上<xref:System.Type?displayProperty=nameWithType>類別中，呼叫共用的方法<xref:System.Type.GetTypeCode%2A>擷取<xref:System.TypeCode>物件類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="1dd72-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="1dd72-109">您可以測試<xref:System.TypeCode>列舉值，針對任何列舉型別成員感興趣，例如`Double`。</span><span class="sxs-lookup"><span data-stu-id="1dd72-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="1dd72-110">若要判斷物件是否相容於指定的型別變數的類型是</span><span class="sxs-lookup"><span data-stu-id="1dd72-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="1dd72-111">使用`TypeOf`運算子結合[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)若要測試的物件`TypeOf`...`Is`運算式。</span><span class="sxs-lookup"><span data-stu-id="1dd72-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="1dd72-112">`TypeOf`...`Is`運算式傳回`True`物件的執行階段類型是否與指定的型別相容。</span><span class="sxs-lookup"><span data-stu-id="1dd72-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="1dd72-113">相容性的條件，取決於指定的型別是類別、 結構或介面。</span><span class="sxs-lookup"><span data-stu-id="1dd72-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="1dd72-114">一般情況下，類型不相容，如果物件是相同的型別、 繼承，或實作指定的型別。</span><span class="sxs-lookup"><span data-stu-id="1dd72-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="1dd72-115">如需詳細資訊，請參閱 < [TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="1dd72-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1dd72-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1dd72-116">Compiling the Code</span></span>  
 <span data-ttu-id="1dd72-117">請注意，變數或運算式，不能指定的型別。</span><span class="sxs-lookup"><span data-stu-id="1dd72-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="1dd72-118">它必須是類型的已定義，例如類別、 結構或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="1dd72-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="1dd72-119">這包括內建類型，例如`Integer`和`String`。</span><span class="sxs-lookup"><span data-stu-id="1dd72-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd72-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd72-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="1dd72-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="1dd72-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="1dd72-122">物件變數值</span><span class="sxs-lookup"><span data-stu-id="1dd72-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="1dd72-123">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="1dd72-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
