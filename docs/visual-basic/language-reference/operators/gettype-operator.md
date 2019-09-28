---
title: GetType 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 2e3e05973f2ef72fef5e429bc98cc58b4b21f2c2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592157"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="b632d-102">GetType 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b632d-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="b632d-103">傳回指定之類型的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="b632d-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="b632d-104">@No__t-0 物件提供類型的相關資訊，例如其屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="b632d-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b632d-105">語法</span><span class="sxs-lookup"><span data-stu-id="b632d-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="b632d-106">參數</span><span class="sxs-lookup"><span data-stu-id="b632d-106">Parameters</span></span>  
  
|<span data-ttu-id="b632d-107">參數</span><span class="sxs-lookup"><span data-stu-id="b632d-107">Parameter</span></span>|<span data-ttu-id="b632d-108">描述</span><span class="sxs-lookup"><span data-stu-id="b632d-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="b632d-109">您想要其資訊的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="b632d-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b632d-110">備註</span><span class="sxs-lookup"><span data-stu-id="b632d-110">Remarks</span></span>  
 <span data-ttu-id="b632d-111">@No__t-0 運算子會針對指定的 `typename` 傳回 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="b632d-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="b632d-112">您可以在 `typename` 中傳遞任何已定義類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="b632d-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="b632d-113">其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="b632d-113">This includes the following:</span></span>  
  
- <span data-ttu-id="b632d-114">任何 Visual Basic 資料類型，例如 `Boolean` 或 `Date`。</span><span class="sxs-lookup"><span data-stu-id="b632d-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="b632d-115">任何 .NET Framework 類別、結構、模組或介面，例如 <xref:System.ArgumentException?displayProperty=nameWithType> 或 <xref:System.Double?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b632d-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="b632d-116">您的應用程式所定義的任何類別、結構、模組或介面。</span><span class="sxs-lookup"><span data-stu-id="b632d-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="b632d-117">您的應用程式所定義的任何陣列。</span><span class="sxs-lookup"><span data-stu-id="b632d-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="b632d-118">您的應用程式所定義的任何委派。</span><span class="sxs-lookup"><span data-stu-id="b632d-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="b632d-119">Visual Basic、.NET Framework 或您的應用程式所定義的任何列舉。</span><span class="sxs-lookup"><span data-stu-id="b632d-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="b632d-120">如果您想要取得物件變數的類型物件，請使用 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b632d-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b632d-121">在下列情況下，`GetType` 運算子可能會很有用：</span><span class="sxs-lookup"><span data-stu-id="b632d-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="b632d-122">您必須在執行時間存取類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b632d-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="b632d-123">@No__t 0 物件提供中繼資料，例如類型成員和部署資訊。</span><span class="sxs-lookup"><span data-stu-id="b632d-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="b632d-124">例如，您需要此來反映元件。</span><span class="sxs-lookup"><span data-stu-id="b632d-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="b632d-125">如需詳細資訊，請參閱<xref:System.Reflection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b632d-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="b632d-126">您想要比較兩個物件參考，以查看它們是否參考相同類型的實例。</span><span class="sxs-lookup"><span data-stu-id="b632d-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="b632d-127">如果有，`GetType` 會傳回相同 <xref:System.Type> 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="b632d-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b632d-128">範例</span><span class="sxs-lookup"><span data-stu-id="b632d-128">Example</span></span>  
 <span data-ttu-id="b632d-129">下列範例顯示使用中的 `GetType` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b632d-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="b632d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b632d-130">See also</span></span>

- [<span data-ttu-id="b632d-131">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="b632d-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b632d-132">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="b632d-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b632d-133">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="b632d-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
