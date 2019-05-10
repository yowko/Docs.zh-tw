---
title: GetType 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 3366a0d1a90667cf1d9b58b211892ad264849c59
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633233"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="5066c-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5066c-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="5066c-103">傳回<xref:System.Type>指定之類型的物件。</span><span class="sxs-lookup"><span data-stu-id="5066c-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="5066c-104"><xref:System.Type>物件提供類型，例如其屬性、 方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5066c-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5066c-105">語法</span><span class="sxs-lookup"><span data-stu-id="5066c-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="5066c-106">參數</span><span class="sxs-lookup"><span data-stu-id="5066c-106">Parameters</span></span>  
  
|<span data-ttu-id="5066c-107">參數</span><span class="sxs-lookup"><span data-stu-id="5066c-107">Parameter</span></span>|<span data-ttu-id="5066c-108">描述</span><span class="sxs-lookup"><span data-stu-id="5066c-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="5066c-109">您想要的資訊類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5066c-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5066c-110">備註</span><span class="sxs-lookup"><span data-stu-id="5066c-110">Remarks</span></span>  
 <span data-ttu-id="5066c-111">`GetType`運算子會傳回<xref:System.Type>所指定的物件`typename`。</span><span class="sxs-lookup"><span data-stu-id="5066c-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="5066c-112">您可以傳遞中任何已定義類型的名稱`typename`。</span><span class="sxs-lookup"><span data-stu-id="5066c-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="5066c-113">其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="5066c-113">This includes the following:</span></span>  
  
- <span data-ttu-id="5066c-114">Visual Basic 中的任何資料類型，例如`Boolean`或`Date`。</span><span class="sxs-lookup"><span data-stu-id="5066c-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="5066c-115">任何.NET Framework 類別、 結構、 模組或介面，例如<xref:System.ArgumentException?displayProperty=nameWithType>或<xref:System.Double?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5066c-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="5066c-116">任何類別、 結構、 模組或應用程式所定義的介面。</span><span class="sxs-lookup"><span data-stu-id="5066c-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="5066c-117">應用程式定義的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="5066c-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="5066c-118">應用程式定義的任何委派。</span><span class="sxs-lookup"><span data-stu-id="5066c-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="5066c-119">Visual Basic、.NET Framework 中或您的應用程式所定義的任何列舉類型。</span><span class="sxs-lookup"><span data-stu-id="5066c-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="5066c-120">如果您想要取得的物件變數的型別物件，使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="5066c-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5066c-121">`GetType`運算子可用於下列情況：</span><span class="sxs-lookup"><span data-stu-id="5066c-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="5066c-122">您必須在執行階段存取類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5066c-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="5066c-123"><xref:System.Type>物件會提供中繼資料，例如型別成員和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="5066c-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="5066c-124">您需要，比方說，以反映的組件。</span><span class="sxs-lookup"><span data-stu-id="5066c-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="5066c-125">如需詳細資訊，請參閱 <xref:System.Reflection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5066c-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="5066c-126">您想要比較兩個物件參考，以查看它們是否參考相同類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5066c-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="5066c-127">如果沒有的話，`GetType`會傳回相同的參考<xref:System.Type>物件。</span><span class="sxs-lookup"><span data-stu-id="5066c-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5066c-128">範例</span><span class="sxs-lookup"><span data-stu-id="5066c-128">Example</span></span>  
 <span data-ttu-id="5066c-129">下列範例會顯示`GetType`中使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="5066c-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="5066c-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5066c-130">See also</span></span>

- [<span data-ttu-id="5066c-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="5066c-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5066c-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="5066c-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5066c-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="5066c-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
