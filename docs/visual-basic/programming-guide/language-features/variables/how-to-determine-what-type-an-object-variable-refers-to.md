---
title: 作法：判斷物件變數所參考的類型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TypeOf operator [Visual Basic], determining object variable type
- variables [Visual Basic], object
- object variables [Visual Basic], determining type
ms.assetid: 6f6a138d-58a4-40d1-9f4e-0a3c598eaf81
ms.openlocfilehash: 935623dd4b6edca188f932aca0e560130199e8f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626577"
---
# <a name="how-to-determine-what-type-an-object-variable-refers-to-visual-basic"></a><span data-ttu-id="359a2-102">作法：判斷物件變數所參考的類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="359a2-102">How to: Determine What Type an Object Variable Refers To (Visual Basic)</span></span>

<span data-ttu-id="359a2-103">物件變數包含儲存在其他位置之資料的指標。</span><span class="sxs-lookup"><span data-stu-id="359a2-103">An object variable contains a pointer to data that is stored elsewhere.</span></span> <span data-ttu-id="359a2-104">該資料的類型可能會在執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="359a2-104">The type of that data can change during run time.</span></span> <span data-ttu-id="359a2-105">您隨時都可以使用<xref:System.Type.GetTypeCode%2A>方法來判斷目前的執行時間型別, 或使用[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)來找出目前的執行時間型別是否與指定的型別相容。</span><span class="sxs-lookup"><span data-stu-id="359a2-105">At any moment, you can use the <xref:System.Type.GetTypeCode%2A> method to determine the current run-time type, or the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to find out if the current run-time type is compatible with a specified type.</span></span>

### <a name="to-determine-the-exact-type-an-object-variable-currently-refers-to"></a><span data-ttu-id="359a2-106">判斷物件變數目前所參考的確切型別</span><span class="sxs-lookup"><span data-stu-id="359a2-106">To determine the exact type an object variable currently refers to</span></span>

1. <span data-ttu-id="359a2-107">在物件變數上, 呼叫<xref:System.Object.GetType%2A>方法以<xref:System.Type?displayProperty=nameWithType>取出物件。</span><span class="sxs-lookup"><span data-stu-id="359a2-107">On the object variable, call the <xref:System.Object.GetType%2A> method to retrieve a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

    ```vb
    Dim myObject As Object
    myObject.GetType()
    ```

2. <span data-ttu-id="359a2-108">在類別上, 呼叫 shared 方法<xref:System.Type.GetTypeCode%2A>以抓取物件類型<xref:System.TypeCode>的列舉值。 <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="359a2-108">On the <xref:System.Type?displayProperty=nameWithType> class, call the shared method <xref:System.Type.GetTypeCode%2A> to retrieve the <xref:System.TypeCode> enumeration value for the object's type.</span></span>

    ```vb
    Dim myObject As Object
    Dim datTyp As Integer = Type.GetTypeCode(myObject.GetType())
    MsgBox("myObject currently has type code " & CStr(datTyp))
    ```

    <span data-ttu-id="359a2-109">您可以針對任何<xref:System.TypeCode>想要的列舉成員 ( `Double`例如) 來測試列舉值。</span><span class="sxs-lookup"><span data-stu-id="359a2-109">You can test the <xref:System.TypeCode> enumeration value against whichever enumeration members are of interest, such as `Double`.</span></span>

### <a name="to-determine-whether-an-object-variables-type-is-compatible-with-a-specified-type"></a><span data-ttu-id="359a2-110">判斷物件變數的類型是否與指定的類型相容</span><span class="sxs-lookup"><span data-stu-id="359a2-110">To determine whether an object variable's type is compatible with a specified type</span></span>

- <span data-ttu-id="359a2-111">使用運算子搭配[Is 運算子](../../../../visual-basic/language-reference/operators/is-operator.md)來測試具有`TypeOf`... 的物件`TypeOf``Is` expression。</span><span class="sxs-lookup"><span data-stu-id="359a2-111">Use the `TypeOf` operator in combination with the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) to test the object with a `TypeOf`...`Is` expression.</span></span>

    ```vb
    If TypeOf objA Is System.Windows.Forms.Control Then
        MsgBox("objA is compatible with the Control class")
    End If
    ```

    <span data-ttu-id="359a2-112">`TypeOf`...`Is` 如果物件的執行時間類型與指定的類型相容,`True`則運算式會傳回。</span><span class="sxs-lookup"><span data-stu-id="359a2-112">The `TypeOf`...`Is` expression returns `True` if the object's run-time type is compatible with the specified type.</span></span>

    <span data-ttu-id="359a2-113">相容性的準則取決於指定的類型是否為類別、結構或介面。</span><span class="sxs-lookup"><span data-stu-id="359a2-113">The criterion for compatibility depends on whether the specified type is a class, structure, or interface.</span></span> <span data-ttu-id="359a2-114">一般而言, 如果物件的類型與相同、繼承自或實作為指定的類型, 則類型是相容的。</span><span class="sxs-lookup"><span data-stu-id="359a2-114">In general, the types are compatible if the object is of the same type as, inherits from, or implements the specified type.</span></span> <span data-ttu-id="359a2-115">如需詳細資訊, 請參閱[TypeOf 運算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="359a2-115">For more information, see [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md).</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="359a2-116">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="359a2-116">Compiling the Code</span></span>

<span data-ttu-id="359a2-117">請注意, 指定的類型不可以是變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="359a2-117">Note that the specified type cannot be a variable or expression.</span></span> <span data-ttu-id="359a2-118">它必須是已定義類型的名稱, 例如類別、結構或介面。</span><span class="sxs-lookup"><span data-stu-id="359a2-118">It must be the name of a defined type, such as a class, structure, or interface.</span></span> <span data-ttu-id="359a2-119">這包括內部類型`Integer` , 例如和。 `String`</span><span class="sxs-lookup"><span data-stu-id="359a2-119">This includes intrinsic types such as `Integer` and `String`.</span></span>

## <a name="see-also"></a><span data-ttu-id="359a2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="359a2-120">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.GetTypeCode%2A>
- <xref:System.TypeCode>
- [<span data-ttu-id="359a2-121">物件變數</span><span class="sxs-lookup"><span data-stu-id="359a2-121">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="359a2-122">物件變數值</span><span class="sxs-lookup"><span data-stu-id="359a2-122">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="359a2-123">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="359a2-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
