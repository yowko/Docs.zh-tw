---
title: "反映 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acfcb519128de0d616757398c94ec70dc7de6ef1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="reflection-visual-basic"></a><span data-ttu-id="3f7d5-102">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f7d5-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="3f7d5-103">反映提供的物件 (型別<xref:System.Type>)，描述組件、 模組和類型。</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="3f7d5-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="3f7d5-104">您可以使用反映來動態建立之型別的執行個體、 繫結類型至現有的物件，或從現有的物件取得類型和叫用其方法或存取其欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="3f7d5-105">如果您在程式碼中使用屬性，則反映可讓您存取它們。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="3f7d5-106">如需詳細資訊，請參閱[屬性](https://msdn.microsoft.com/library/5x6cd29c)。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="3f7d5-107">以下是反映和使用靜態方法的簡單範例`GetType`-從所有型別繼承`Object`基底類別-若要取得變數的型別︰</span><span class="sxs-lookup"><span data-stu-id="3f7d5-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="3f7d5-108">輸出如下︰</span><span class="sxs-lookup"><span data-stu-id="3f7d5-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="3f7d5-109">下列範例會使用反映取得載入的組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="3f7d5-110">輸出如下︰</span><span class="sxs-lookup"><span data-stu-id="3f7d5-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="3f7d5-111">反映概觀</span><span class="sxs-lookup"><span data-stu-id="3f7d5-111">Reflection Overview</span></span>  
 <span data-ttu-id="3f7d5-112">反映適合在下列情況︰</span><span class="sxs-lookup"><span data-stu-id="3f7d5-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="3f7d5-113">當您需要存取您的程式中繼資料屬性。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="3f7d5-114">如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-114">For more information, see [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span></span>  
  
-   <span data-ttu-id="3f7d5-115">檢查與組件中的型別具現化。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="3f7d5-116">建立新的型別在執行階段。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-116">For building new types at runtime.</span></span> <span data-ttu-id="3f7d5-117">使用中<xref:System.Reflection.Emit>.</xref:System.Reflection.Emit>類別</span><span class="sxs-lookup"><span data-stu-id="3f7d5-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="3f7d5-118">用於執行晚期繫結，存取執行階段建立型別的方法。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="3f7d5-119">請參閱主題[動態載入和使用型別](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc)。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-119">See the topic [Dynamically Loading and Using Types](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3f7d5-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="3f7d5-120">Related Sections</span></span>  
 <span data-ttu-id="3f7d5-121">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="3f7d5-121">For more information:</span></span>  
  
-   [<span data-ttu-id="3f7d5-122">反映</span><span class="sxs-lookup"><span data-stu-id="3f7d5-122">Reflection</span></span>](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [<span data-ttu-id="3f7d5-123">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="3f7d5-123">Viewing Type Information</span></span>](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [<span data-ttu-id="3f7d5-124">反映和泛用型別</span><span class="sxs-lookup"><span data-stu-id="3f7d5-124">Reflection and Generic Types</span></span>](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <span data-ttu-id="3f7d5-125"><xref:System.Reflection.Emit></xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="3f7d5-125"><xref:System.Reflection.Emit></span></span>  
  
-   [<span data-ttu-id="3f7d5-126">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="3f7d5-126">Retrieving Information Stored in Attributes</span></span>](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a><span data-ttu-id="3f7d5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f7d5-127">See Also</span></span>  
 <span data-ttu-id="3f7d5-128">[Visual Basic 程式設計指南](../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f7d5-128">[Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="3f7d5-129"> [Common Language Runtime 中的組件](https://msdn.microsoft.com/library/k3677y81)</span><span class="sxs-lookup"><span data-stu-id="3f7d5-129"> [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span></span>
