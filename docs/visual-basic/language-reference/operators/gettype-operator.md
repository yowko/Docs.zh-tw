---
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349555"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="d45b6-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d45b6-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="d45b6-103">Returns a <xref:System.Type> object for the specified type.</span><span class="sxs-lookup"><span data-stu-id="d45b6-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="d45b6-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span><span class="sxs-lookup"><span data-stu-id="d45b6-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d45b6-105">語法</span><span class="sxs-lookup"><span data-stu-id="d45b6-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="d45b6-106">參數</span><span class="sxs-lookup"><span data-stu-id="d45b6-106">Parameters</span></span>  
  
|<span data-ttu-id="d45b6-107">參數</span><span class="sxs-lookup"><span data-stu-id="d45b6-107">Parameter</span></span>|<span data-ttu-id="d45b6-108">描述</span><span class="sxs-lookup"><span data-stu-id="d45b6-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="d45b6-109">The name of the type for which you desire information.</span><span class="sxs-lookup"><span data-stu-id="d45b6-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d45b6-110">備註</span><span class="sxs-lookup"><span data-stu-id="d45b6-110">Remarks</span></span>  
 <span data-ttu-id="d45b6-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span><span class="sxs-lookup"><span data-stu-id="d45b6-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="d45b6-112">You can pass the name of any defined type in `typename`.</span><span class="sxs-lookup"><span data-stu-id="d45b6-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="d45b6-113">其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="d45b6-113">This includes the following:</span></span>  
  
- <span data-ttu-id="d45b6-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span><span class="sxs-lookup"><span data-stu-id="d45b6-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="d45b6-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d45b6-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="d45b6-116">Any class, structure, module, or interface defined by your application.</span><span class="sxs-lookup"><span data-stu-id="d45b6-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="d45b6-117">Any array defined by your application.</span><span class="sxs-lookup"><span data-stu-id="d45b6-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="d45b6-118">Any delegate defined by your application.</span><span class="sxs-lookup"><span data-stu-id="d45b6-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="d45b6-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span><span class="sxs-lookup"><span data-stu-id="d45b6-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="d45b6-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span><span class="sxs-lookup"><span data-stu-id="d45b6-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="d45b6-121">The `GetType` operator can be useful in the following circumstances:</span><span class="sxs-lookup"><span data-stu-id="d45b6-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="d45b6-122">You must access the metadata for a type at run time.</span><span class="sxs-lookup"><span data-stu-id="d45b6-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="d45b6-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span><span class="sxs-lookup"><span data-stu-id="d45b6-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="d45b6-124">You need this, for example, to reflect over an assembly.</span><span class="sxs-lookup"><span data-stu-id="d45b6-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="d45b6-125">如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d45b6-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="d45b6-126">You want to compare two object references to see if they refer to instances of the same type.</span><span class="sxs-lookup"><span data-stu-id="d45b6-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="d45b6-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span><span class="sxs-lookup"><span data-stu-id="d45b6-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d45b6-128">範例</span><span class="sxs-lookup"><span data-stu-id="d45b6-128">Example</span></span>  
 <span data-ttu-id="d45b6-129">The following examples show the `GetType` operator in use.</span><span class="sxs-lookup"><span data-stu-id="d45b6-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="d45b6-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="d45b6-130">See also</span></span>

- [<span data-ttu-id="d45b6-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="d45b6-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="d45b6-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="d45b6-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="d45b6-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="d45b6-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
