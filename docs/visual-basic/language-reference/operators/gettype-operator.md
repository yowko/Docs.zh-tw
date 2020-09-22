---
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 9ff207ea4f2b89ea30eb8f46a3e640ccf3789974
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867011"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="43156-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43156-102">GetType Operator (Visual Basic)</span></span>

<span data-ttu-id="43156-103">傳回 <xref:System.Type> 指定類型的物件。</span><span class="sxs-lookup"><span data-stu-id="43156-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="43156-104"><xref:System.Type>物件會提供類型的相關資訊，例如其屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="43156-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43156-105">語法</span><span class="sxs-lookup"><span data-stu-id="43156-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="43156-106">參數</span><span class="sxs-lookup"><span data-stu-id="43156-106">Parameters</span></span>  
  
|<span data-ttu-id="43156-107">參數</span><span class="sxs-lookup"><span data-stu-id="43156-107">Parameter</span></span>|<span data-ttu-id="43156-108">Description</span><span class="sxs-lookup"><span data-stu-id="43156-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="43156-109">您想要其資訊的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="43156-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43156-110">備註</span><span class="sxs-lookup"><span data-stu-id="43156-110">Remarks</span></span>  

 <span data-ttu-id="43156-111">運算子會傳回指定之的 `GetType` <xref:System.Type> 物件 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="43156-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="43156-112">您可以在中傳遞任何已定義類型的名稱 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="43156-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="43156-113">其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="43156-113">This includes the following:</span></span>  
  
- <span data-ttu-id="43156-114">任何 Visual Basic 資料類型，例如 `Boolean` 或 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="43156-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="43156-115">任何 .NET Framework 類別、結構、模組或介面，例如 <xref:System.ArgumentException?displayProperty=nameWithType> 或 <xref:System.Double?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="43156-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="43156-116">應用程式所定義的任何類別、結構、模組或介面。</span><span class="sxs-lookup"><span data-stu-id="43156-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="43156-117">應用程式所定義的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="43156-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="43156-118">您的應用程式所定義的任何委派。</span><span class="sxs-lookup"><span data-stu-id="43156-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="43156-119">由 Visual Basic、.NET Framework 或您的應用程式所定義的任何列舉。</span><span class="sxs-lookup"><span data-stu-id="43156-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="43156-120">如果您想要取得物件變數的型別物件，請使用 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="43156-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="43156-121">在 `GetType` 下列情況下，運算子可能很有用：</span><span class="sxs-lookup"><span data-stu-id="43156-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="43156-122">您必須在執行時間存取類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="43156-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="43156-123"><xref:System.Type>物件提供中繼資料，例如類型成員和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="43156-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="43156-124">例如，您需要此範例以反映元件。</span><span class="sxs-lookup"><span data-stu-id="43156-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="43156-125">如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="43156-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="43156-126">您想要比較兩個物件參考，看看它們是否參考相同類型的實例。</span><span class="sxs-lookup"><span data-stu-id="43156-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="43156-127">如果有的話，會傳回 `GetType` 相同物件的參考 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="43156-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43156-128">範例</span><span class="sxs-lookup"><span data-stu-id="43156-128">Example</span></span>  

 <span data-ttu-id="43156-129">下列範例顯示 `GetType` 使用中的運算子。</span><span class="sxs-lookup"><span data-stu-id="43156-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="43156-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43156-130">See also</span></span>

- [<span data-ttu-id="43156-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="43156-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="43156-132">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="43156-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="43156-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="43156-133">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
