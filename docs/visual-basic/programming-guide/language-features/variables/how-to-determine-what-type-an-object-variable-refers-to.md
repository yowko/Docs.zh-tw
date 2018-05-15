---
title: 如何：決定物件變數參考的類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 0dfd4ed87b65f536802ae71cbc3de41e1c4f83af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="3f1eb-102">如何：決定物件變數參考的類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f1eb-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>
<span data-ttu-id="3f1eb-103">物件變數包含儲存在其他位置的資料指標。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="3f1eb-104">在執行階段可以變更該資料的類型。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-104">The type of that data can change during run time.</span></span> <span data-ttu-id="3f1eb-105">在任何時刻，您可以使用<xref:System.Type.GetTypeCode%2A>方法，以判斷目前的執行階段類型，或[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來找出是否有目前執行階段型別是使用指定的型別相容。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>  
  
### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="3f1eb-106">若要判斷的確切型別物件變數目前參考</span><span class="sxs-lookup"><span data-stu-id="3f1eb-106">To determine the exact type an object variable currently refers to</span></span>  
  
1.  <span data-ttu-id="3f1eb-107">物件變數上呼叫<xref:System.Object.GetType%2A>方法來擷取<xref:System.Type?displayProperty=nameWithType>物件。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
    ```  
    Dim myObject As Object  
    myObject.GetType()  
    ```  
  
2.  <span data-ttu-id="3f1eb-108">在<xref:System.Type?displayProperty=nameWithType>類別，呼叫共用的方法<xref:System.Type.GetTypeCode%2A>擷取<xref:System.TypeCode>的物件類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>  
  
    ```  
    Dim myObject As Object  
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())  
    MsgBox("myObject currently has type code " & CStr(datTyp))  
    ```  
  
     <span data-ttu-id="3f1eb-109">您可以測試<xref:System.TypeCode>列舉值，針對任何列舉型別成員感興趣，例如`Double`。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>  
  
### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="3f1eb-110">若要判斷物件是否與指定的型別相容變數的類型是</span><span class="sxs-lookup"><span data-stu-id="3f1eb-110">To determine whether an object variable's type is compatible with a specified type</span></span>  
  
-   <span data-ttu-id="3f1eb-111">使用`TypeOf`運算子結合[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)來測試與物件`TypeOf`...`Is`運算式。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>  
  
    ```  
    If TypeOf objA Is System.Windows.Forms.Control Then  
        MsgBox("objA is compatible with the Control class")  
    End If  
    ```  
  
     <span data-ttu-id="3f1eb-112">`TypeOf`...`Is`運算式傳回`True`物件的執行階段類型是否與指定的型別相容。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>  
  
     <span data-ttu-id="3f1eb-113">相容性的條件取決於是否指定的型別是類別、 結構或介面。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="3f1eb-114">一般情況下的類型相容，如果物件為相同的型別、 繼承自或實作指定的型別。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="3f1eb-115">如需詳細資訊，請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3f1eb-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="3f1eb-116">Compiling the Code</span></span>  
 <span data-ttu-id="3f1eb-117">請注意，指定的型別不可以變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="3f1eb-118">它必須是已定義的類型，例如類別、 結構或介面名稱。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="3f1eb-119">這包含內建型別，例如`Integer`和`String`。</span><span class="sxs-lookup"><span data-stu-id="3f1eb-119">This includes intrinsic types such as `Integer` and `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1eb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f1eb-120">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.GetTypeCode%2A>  
 <xref:System.TypeCode>  
 [<span data-ttu-id="3f1eb-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="3f1eb-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="3f1eb-122">物件變數值</span><span class="sxs-lookup"><span data-stu-id="3f1eb-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="3f1eb-123">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="3f1eb-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
