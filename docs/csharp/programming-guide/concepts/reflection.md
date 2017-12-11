---
title: "反映 (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f80a2362-953b-4e8e-9759-cd5f334190d4
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68a586fd8a8a8fbe6e351efa3e51c5ba1d2ff4d7
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="reflection-c"></a><span data-ttu-id="1bb00-102">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="1bb00-102">Reflection (C#)</span></span>
<span data-ttu-id="1bb00-103">反映提供的物件 (類型為 <xref:System.Type>) 可描述組件、模組和類型。</span><span class="sxs-lookup"><span data-stu-id="1bb00-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="1bb00-104">您可以使用反映來動態建立類型的執行個體、將類型繫結至現有的物件，或從現有的物件取得類型，並叫用其方法或存取其欄位及屬性。</span><span class="sxs-lookup"><span data-stu-id="1bb00-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="1bb00-105">如果您在程式碼中使用屬性，則反映可讓您存取它們。</span><span class="sxs-lookup"><span data-stu-id="1bb00-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="1bb00-106">如需詳細資訊，請參閱[屬性](../../../../docs/standard/attributes/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb00-106">For more information, see [Attributes](../../../../docs/standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="1bb00-107">以下簡單反映範例使用 `Object` 基底類別的所有類型所繼承的靜態方法 `GetType` 來取得變數的類型︰</span><span class="sxs-lookup"><span data-stu-id="1bb00-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```csharp  
// Using GetType to obtain type information:  
int i = 42;  
System.Type type = i.GetType();  
System.Console.WriteLine(type);  
```  
  
 <span data-ttu-id="1bb00-108">輸出為：</span><span class="sxs-lookup"><span data-stu-id="1bb00-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="1bb00-109">下列範例使用反映以取得所載入組件的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="1bb00-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```csharp  
// Using Reflection to get information from an Assembly:  
System.Reflection.Assembly info = typeof(System.Int32).Assembly;  
System.Console.WriteLine(info);  
```  
  
 <span data-ttu-id="1bb00-110">輸出為：</span><span class="sxs-lookup"><span data-stu-id="1bb00-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
> [!NOTE]
>  <span data-ttu-id="1bb00-111">C# 關鍵字 `protected` 和 `internal` 在 IL 中沒有任何意義，而且不會用於反映 API 中。</span><span class="sxs-lookup"><span data-stu-id="1bb00-111">The C# keywords `protected` and `internal` have no meaning in IL and are not used in the reflection APIs.</span></span> <span data-ttu-id="1bb00-112">IL 中的對應詞彙是「系列」和「組件」。</span><span class="sxs-lookup"><span data-stu-id="1bb00-112">The corresponding terms in IL are *Family* and *Assembly*.</span></span> <span data-ttu-id="1bb00-113">若要使用反映來識別 `internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsAssembly%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="1bb00-113">To identify an `internal` method using reflection, use the <xref:System.Reflection.MethodBase.IsAssembly%2A> property.</span></span> <span data-ttu-id="1bb00-114">若要識別 `protected internal` 方法，請使用 <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>。</span><span class="sxs-lookup"><span data-stu-id="1bb00-114">To identify a `protected internal` method, use the <xref:System.Reflection.MethodBase.IsFamilyOrAssembly%2A>.</span></span>  
  
## <a name="reflection-overview"></a><span data-ttu-id="1bb00-115">反映概觀</span><span class="sxs-lookup"><span data-stu-id="1bb00-115">Reflection Overview</span></span>  
 <span data-ttu-id="1bb00-116">反映在下列情況下十分有用：</span><span class="sxs-lookup"><span data-stu-id="1bb00-116">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="1bb00-117">當您需要存取程式中繼資料中的屬性時。</span><span class="sxs-lookup"><span data-stu-id="1bb00-117">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="1bb00-118">如需詳細資訊，請參閱[擷取儲存於屬性中的資訊](../../../standard/attributes/retrieving-information-stored-in-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="1bb00-118">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
-   <span data-ttu-id="1bb00-119">如需檢查和具現化組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="1bb00-119">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="1bb00-120">如需在執行階段建置新類型。</span><span class="sxs-lookup"><span data-stu-id="1bb00-120">For building new types at runtime.</span></span> <span data-ttu-id="1bb00-121">使用 <xref:System.Reflection.Emit> 中的類別。</span><span class="sxs-lookup"><span data-stu-id="1bb00-121">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="1bb00-122">對於執行晚期繫結，存取在執行階段建立的類型上的方法。</span><span class="sxs-lookup"><span data-stu-id="1bb00-122">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="1bb00-123">請參閱[動態載入和使用類型](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1bb00-123">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1bb00-124">相關章節</span><span class="sxs-lookup"><span data-stu-id="1bb00-124">Related Sections</span></span>  
 <span data-ttu-id="1bb00-125">如需詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="1bb00-125">For more information:</span></span>  
  
-   [<span data-ttu-id="1bb00-126">反映</span><span class="sxs-lookup"><span data-stu-id="1bb00-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
-   [<span data-ttu-id="1bb00-127">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="1bb00-127">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
-   [<span data-ttu-id="1bb00-128">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="1bb00-128">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
-   <xref:System.Reflection.Emit>  
  
-   [<span data-ttu-id="1bb00-129">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="1bb00-129">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="1bb00-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bb00-130">See Also</span></span>  
 [<span data-ttu-id="1bb00-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1bb00-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1bb00-132">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="1bb00-132">Assemblies in the Common Language Runtime</span></span>](../../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
