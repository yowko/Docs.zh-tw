---
title: 反映 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: d2ad8957d308aa98935c862ec1864b6682be904b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834877"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="b9ce1-102">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9ce1-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="b9ce1-103">反映提供的物件 (類型為 <xref:System.Type>) 可描述組件、模組和類型。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="b9ce1-104">您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b9ce1-105">如果您在程式碼中使用屬性，則反映可讓您存取它們。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b9ce1-106">如需詳細資訊，請參閱[屬性](../../../standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="b9ce1-107">以下簡單反映範例使用 `Object` 基底類別的所有類型所繼承的靜態方法 `GetType` 來取得變數的類型︰</span><span class="sxs-lookup"><span data-stu-id="b9ce1-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="b9ce1-108">輸出為：</span><span class="sxs-lookup"><span data-stu-id="b9ce1-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="b9ce1-109">下列範例使用反映以取得所載入組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="b9ce1-110">輸出為：</span><span class="sxs-lookup"><span data-stu-id="b9ce1-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="b9ce1-111">反映概觀</span><span class="sxs-lookup"><span data-stu-id="b9ce1-111">Reflection Overview</span></span>  
 <span data-ttu-id="b9ce1-112">反映在下列情況下十分有用：</span><span class="sxs-lookup"><span data-stu-id="b9ce1-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="b9ce1-113">當您需要存取程式中繼資料中的屬性時。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b9ce1-114">如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="b9ce1-115">如需檢查和具現化組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="b9ce1-116">如需在執行階段建置新類型。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-116">For building new types at runtime.</span></span> <span data-ttu-id="b9ce1-117">使用 <xref:System.Reflection.Emit> 中的類別。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="b9ce1-118">對於執行晚期繫結，存取在執行階段建立的類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b9ce1-119">請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="b9ce1-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9ce1-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="b9ce1-120">Related Sections</span></span>  
 <span data-ttu-id="b9ce1-121">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="b9ce1-121">For more information:</span></span>  
  
-   [<span data-ttu-id="b9ce1-122">反映</span><span class="sxs-lookup"><span data-stu-id="b9ce1-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="b9ce1-123">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="b9ce1-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="b9ce1-124">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="b9ce1-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="b9ce1-125">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="b9ce1-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="b9ce1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9ce1-126">See also</span></span>

- [<span data-ttu-id="b9ce1-127">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b9ce1-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="b9ce1-128">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="b9ce1-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
