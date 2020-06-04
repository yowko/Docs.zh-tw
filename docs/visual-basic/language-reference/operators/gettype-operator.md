---
title: GetType Operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 37644a9c37ffde084120c5f1e1ee8c87a04ffc3c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371151"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="1aac3-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1aac3-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="1aac3-103">傳回 <xref:System.Type> 指定之類型的物件。</span><span class="sxs-lookup"><span data-stu-id="1aac3-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="1aac3-104"><xref:System.Type>物件會提供類型的相關資訊，例如其屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="1aac3-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aac3-105">語法</span><span class="sxs-lookup"><span data-stu-id="1aac3-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aac3-106">參數</span><span class="sxs-lookup"><span data-stu-id="1aac3-106">Parameters</span></span>  
  
|<span data-ttu-id="1aac3-107">參數</span><span class="sxs-lookup"><span data-stu-id="1aac3-107">Parameter</span></span>|<span data-ttu-id="1aac3-108">說明</span><span class="sxs-lookup"><span data-stu-id="1aac3-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="1aac3-109">您想要其資訊的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="1aac3-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aac3-110">備註</span><span class="sxs-lookup"><span data-stu-id="1aac3-110">Remarks</span></span>  
 <span data-ttu-id="1aac3-111">運算子會傳回 `GetType` <xref:System.Type> 所指定的物件 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="1aac3-112">您可以在中傳遞任何已定義類型的名稱 `typename` 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="1aac3-113">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="1aac3-113">This includes the following:</span></span>  
  
- <span data-ttu-id="1aac3-114">任何 Visual Basic 資料類型，例如 `Boolean` 或 `Date` 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="1aac3-115">任何 .NET Framework 類別、結構、模組或介面，例如 <xref:System.ArgumentException?displayProperty=nameWithType> 或 <xref:System.Double?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1aac3-116">您的應用程式所定義的任何類別、結構、模組或介面。</span><span class="sxs-lookup"><span data-stu-id="1aac3-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="1aac3-117">您的應用程式所定義的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="1aac3-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="1aac3-118">您的應用程式所定義的任何委派。</span><span class="sxs-lookup"><span data-stu-id="1aac3-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="1aac3-119">Visual Basic、.NET Framework 或您的應用程式所定義的任何列舉。</span><span class="sxs-lookup"><span data-stu-id="1aac3-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="1aac3-120">如果您想要取得物件變數的型別物件，請使用 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="1aac3-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1aac3-121">在 `GetType` 下列情況下，運算子可能會很有用：</span><span class="sxs-lookup"><span data-stu-id="1aac3-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="1aac3-122">您必須在執行時間存取類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="1aac3-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="1aac3-123"><xref:System.Type>物件提供中繼資料，例如類型成員和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="1aac3-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="1aac3-124">例如，您需要此來反映元件。</span><span class="sxs-lookup"><span data-stu-id="1aac3-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="1aac3-125">如需詳細資訊，請參閱 <xref:System.Reflection?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="1aac3-126">您想要比較兩個物件參考，以查看它們是否參考相同類型的實例。</span><span class="sxs-lookup"><span data-stu-id="1aac3-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="1aac3-127">如果有的話，會傳回 `GetType` 相同物件的參考 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="1aac3-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1aac3-128">範例</span><span class="sxs-lookup"><span data-stu-id="1aac3-128">Example</span></span>  
 <span data-ttu-id="1aac3-129">下列範例顯示 `GetType` 使用中的運算子。</span><span class="sxs-lookup"><span data-stu-id="1aac3-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="1aac3-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aac3-130">See also</span></span>

- [<span data-ttu-id="1aac3-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="1aac3-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1aac3-132">依功能列出運算子</span><span class="sxs-lookup"><span data-stu-id="1aac3-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1aac3-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="1aac3-133">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
