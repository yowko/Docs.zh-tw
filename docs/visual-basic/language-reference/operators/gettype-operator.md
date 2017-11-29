---
title: "GetType 運算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="14e6e-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14e6e-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="14e6e-103">傳回<xref:System.Type>指定類型的物件。</span><span class="sxs-lookup"><span data-stu-id="14e6e-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="14e6e-104"><xref:System.Type>物件提供類型，例如其屬性、 方法和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="14e6e-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14e6e-105">語法</span><span class="sxs-lookup"><span data-stu-id="14e6e-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14e6e-106">參數</span><span class="sxs-lookup"><span data-stu-id="14e6e-106">Parameters</span></span>  
  
|<span data-ttu-id="14e6e-107">參數</span><span class="sxs-lookup"><span data-stu-id="14e6e-107">Parameter</span></span>|<span data-ttu-id="14e6e-108">說明</span><span class="sxs-lookup"><span data-stu-id="14e6e-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="14e6e-109">您想要的資訊類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="14e6e-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14e6e-110">備註</span><span class="sxs-lookup"><span data-stu-id="14e6e-110">Remarks</span></span>  
 <span data-ttu-id="14e6e-111">`GetType`運算子會傳回<xref:System.Type>物件指定`typename`。</span><span class="sxs-lookup"><span data-stu-id="14e6e-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="14e6e-112">您可以傳遞任何已定義型別的名稱`typename`。</span><span class="sxs-lookup"><span data-stu-id="14e6e-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="14e6e-113">其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="14e6e-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="14e6e-114">Visual Basic 中的任何資料類型，例如`Boolean`或`Date`。</span><span class="sxs-lookup"><span data-stu-id="14e6e-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="14e6e-115">任何.NET Framework 類別、 結構、 模組或介面，例如<xref:System.ArgumentException?displayProperty=nameWithType>或<xref:System.Double?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="14e6e-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="14e6e-116">任何類別、 結構、 模組或應用程式所定義的介面。</span><span class="sxs-lookup"><span data-stu-id="14e6e-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="14e6e-117">應用程式所定義的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="14e6e-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="14e6e-118">任何應用程式所定義的委派。</span><span class="sxs-lookup"><span data-stu-id="14e6e-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="14e6e-119">Visual Basic、.NET Framework 中或您的應用程式所定義的任何列舉類型。</span><span class="sxs-lookup"><span data-stu-id="14e6e-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="14e6e-120">如果您想要取得之物件變數的型別物件，使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="14e6e-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="14e6e-121">`GetType`運算子只能在下列情況下很有用：</span><span class="sxs-lookup"><span data-stu-id="14e6e-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="14e6e-122">您必須在執行階段存取類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="14e6e-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="14e6e-123"><xref:System.Type>物件會提供中繼資料，例如型別成員和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="14e6e-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="14e6e-124">您需要此，例如，以反映透過組件。</span><span class="sxs-lookup"><span data-stu-id="14e6e-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="14e6e-125">如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="14e6e-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="14e6e-126">您想要比較兩個物件參考，以查看它們是否參考相同類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="14e6e-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="14e6e-127">如果沒有的話，`GetType`傳回相同的參考<xref:System.Type>物件。</span><span class="sxs-lookup"><span data-stu-id="14e6e-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14e6e-128">範例</span><span class="sxs-lookup"><span data-stu-id="14e6e-128">Example</span></span>  
 <span data-ttu-id="14e6e-129">下列範例會顯示`GetType`中使用的運算子。</span><span class="sxs-lookup"><span data-stu-id="14e6e-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="14e6e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14e6e-130">See Also</span></span>  
 [<span data-ttu-id="14e6e-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="14e6e-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="14e6e-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="14e6e-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="14e6e-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="14e6e-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
