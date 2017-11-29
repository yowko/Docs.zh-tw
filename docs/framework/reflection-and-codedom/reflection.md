---
title: ".NET Framework 中的反映"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c2d95bfae212f658945904a647885ebd303cbc7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reflection-in-the-net-framework"></a><span data-ttu-id="56225-102">.NET Framework 中的反映</span><span class="sxs-lookup"><span data-stu-id="56225-102">Reflection in the .NET Framework</span></span>
<span data-ttu-id="56225-103"><xref:System.Reflection> 命名空間中的類別，連同 <xref:System.Type?displayProperty=nameWithType>，可讓您取得已載入[組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)和其中所定義類型的資訊，例如[類別](http://msdn.microsoft.com/en-us/ad7d3561-271e-4546-82fc-e00b059f27a9)、[介面](http://msdn.microsoft.com/en-us/fd9d5975-5363-4bc9-b883-609f887895e5)和[實值型別](http://msdn.microsoft.com/en-us/c9c567f8-8ab1-4d88-834d-00f7d92418de)。</span><span class="sxs-lookup"><span data-stu-id="56225-103">The classes in the <xref:System.Reflection> namespace, together with <xref:System.Type?displayProperty=nameWithType>, enable you to obtain information about loaded [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) and the types defined within them, such as [classes](http://msdn.microsoft.com/en-us/ad7d3561-271e-4546-82fc-e00b059f27a9), [interfaces](http://msdn.microsoft.com/en-us/fd9d5975-5363-4bc9-b883-609f887895e5), and [value types](http://msdn.microsoft.com/en-us/c9c567f8-8ab1-4d88-834d-00f7d92418de).</span></span> <span data-ttu-id="56225-104">您也可以使用反映在執行階段建立類型執行個體，並叫用和存取它們。</span><span class="sxs-lookup"><span data-stu-id="56225-104">You can also use reflection to create type instances at run time, and to invoke and access them.</span></span> <span data-ttu-id="56225-105">如需反映特定層面的主題，請參閱此概觀結尾的[相關主題](#related_topics)。</span><span class="sxs-lookup"><span data-stu-id="56225-105">For topics about specific aspects of reflection, see [Related Topics](#related_topics) at the end of this overview.</span></span>  
  
 <span data-ttu-id="56225-106">[Common Language Runtime](../../../docs/standard/clr.md) 載入器會管理[應用程式定義域](../../../docs/framework/app-domains/application-domains.md)，這會在有相同應用程式範圍的物件周圍構成定義的界限。</span><span class="sxs-lookup"><span data-stu-id="56225-106">The [common language runtime](../../../docs/standard/clr.md) loader manages [application domains](../../../docs/framework/app-domains/application-domains.md), which constitute defined boundaries around objects that have the same application scope.</span></span> <span data-ttu-id="56225-107">這個管理包含載入每個組件至適當的應用程式定義域和控制每個組件內類型階層的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="56225-107">This management includes loading each assembly into the appropriate application domain and controlling the memory layout of the type hierarchy within each assembly.</span></span>  
  
 <span data-ttu-id="56225-108">[組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)包含模組、模組包含類型，而類型包含成員。</span><span class="sxs-lookup"><span data-stu-id="56225-108">[Assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) contain modules, modules contain types, and types contain members.</span></span> <span data-ttu-id="56225-109">反映提供封裝組件、模組和類型的物件。</span><span class="sxs-lookup"><span data-stu-id="56225-109">Reflection provides objects that encapsulate assemblies, modules, and types.</span></span> <span data-ttu-id="56225-110">您可以使用反映來動態建立類型的執行個體、繫結類型至現有的物件，或從現有的物件取得類型。</span><span class="sxs-lookup"><span data-stu-id="56225-110">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object.</span></span> <span data-ttu-id="56225-111">然後，您可以叫用類型的方法或存取其欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="56225-111">You can then invoke the type's methods or access its fields and properties.</span></span> <span data-ttu-id="56225-112">反映的一般用法包含下列幾項：</span><span class="sxs-lookup"><span data-stu-id="56225-112">Typical uses of reflection include the following:</span></span>  
  
-   <span data-ttu-id="56225-113">使用 <xref:System.Reflection.Assembly> 來定義和載入組件，載入列在組件資訊清單中的模組，然後從這個組件中尋找類型並建立它的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56225-113">Use <xref:System.Reflection.Assembly> to define and load assemblies, load modules that are listed in the assembly manifest, and locate a type from this assembly and create an instance of it.</span></span>  
  
-   <span data-ttu-id="56225-114">使用 <xref:System.Reflection.Module> 來探索資訊，例如包含模組的組件以及模組中的類別。</span><span class="sxs-lookup"><span data-stu-id="56225-114">Use <xref:System.Reflection.Module> to discover information such as the assembly that contains the module and the classes in the module.</span></span> <span data-ttu-id="56225-115">您也可以取得所有全域方法，或在模組上所定義的其他特定非全域方法。</span><span class="sxs-lookup"><span data-stu-id="56225-115">You can also get all global methods or other specific, nonglobal methods defined on the module.</span></span>  
  
-   <span data-ttu-id="56225-116">使用 <xref:System.Reflection.ConstructorInfo> 來探索資訊，例如名稱、參數、存取修飾詞 (例如 `public` 或 `private`)，以及建構函式的實作詳細資料 (例如 `abstract` 或 `virtual`)。</span><span class="sxs-lookup"><span data-stu-id="56225-116">Use <xref:System.Reflection.ConstructorInfo> to discover information such as the name, parameters, access modifiers (such as `public` or `private`), and implementation details (such as `abstract` or `virtual`) of a constructor.</span></span> <span data-ttu-id="56225-117">使用 <xref:System.Type> 的 <xref:System.Type.GetConstructors%2A> 或 <xref:System.Type.GetConstructor%2A> 方法來叫用特定的建構函式。</span><span class="sxs-lookup"><span data-stu-id="56225-117">Use the <xref:System.Type.GetConstructors%2A> or <xref:System.Type.GetConstructor%2A> method of a <xref:System.Type> to invoke a specific constructor.</span></span>  
  
-   <span data-ttu-id="56225-118">使用 <xref:System.Reflection.MethodInfo> 來探索資訊，例如名稱、傳回類型、參數、存取修飾詞 (例如 `public` 或 `private`)，以及方法的實作詳細資料 (例如 `abstract` 或 `virtual`)。</span><span class="sxs-lookup"><span data-stu-id="56225-118">Use <xref:System.Reflection.MethodInfo> to discover information such as the name, return type, parameters, access modifiers (such as `public` or `private`), and implementation details (such as `abstract` or `virtual`) of a method.</span></span> <span data-ttu-id="56225-119">使用 <xref:System.Type> 的 <xref:System.Type.GetMethods%2A> 或 <xref:System.Type.GetMethod%2A> 方法來叫用特定的方法。</span><span class="sxs-lookup"><span data-stu-id="56225-119">Use the <xref:System.Type.GetMethods%2A> or <xref:System.Type.GetMethod%2A> method of a <xref:System.Type> to invoke a specific method.</span></span>  
  
-   <span data-ttu-id="56225-120">使用 <xref:System.Reflection.FieldInfo> 來探索資訊，例如名稱、存取修飾詞 (例如 `public` 或 `private`)，以及欄位的實作詳細資料 (例如 `static`)，並取得或設定欄位值。</span><span class="sxs-lookup"><span data-stu-id="56225-120">Use <xref:System.Reflection.FieldInfo> to discover information such as the name, access modifiers (such as `public` or `private`) and implementation details (such as `static`) of a field, and to get or set field values.</span></span>  
  
-   <span data-ttu-id="56225-121">使用 <xref:System.Reflection.EventInfo> 來探索資訊，例如名稱、事件處理常式資料類型、自訂屬性、宣告類型，以及事件的反映類型，並加入或移除事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="56225-121">Use <xref:System.Reflection.EventInfo> to discover information such as the name, event-handler data type, custom attributes, declaring type, and reflected type of an event, and to add or remove event handlers.</span></span>  
  
-   <span data-ttu-id="56225-122">使用 <xref:System.Reflection.PropertyInfo> 來探索資訊，例如名稱、資料類型、宣告類型、反映類型和唯讀或可寫入的屬性狀態，並且取得或設定屬性值。</span><span class="sxs-lookup"><span data-stu-id="56225-122">Use <xref:System.Reflection.PropertyInfo> to discover information such as the name, data type, declaring type, reflected type, and read-only or writable status of a property, and to get or set property values.</span></span>  
  
-   <span data-ttu-id="56225-123">使用 <xref:System.Reflection.ParameterInfo> 來探索資訊，例如參數的名稱、資料類型、參數是否為輸入或輸出參數以及方法簽章中的參數位置。</span><span class="sxs-lookup"><span data-stu-id="56225-123">Use <xref:System.Reflection.ParameterInfo> to discover information such as a parameter's name, data type, whether a parameter is an input or output parameter, and the position of the parameter in a method signature.</span></span>  
  
-   <span data-ttu-id="56225-124">當您在應用程式定義域的僅限反映之內容中工作時，請使用 <xref:System.Reflection.CustomAttributeData> 來探索自訂屬性的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="56225-124">Use <xref:System.Reflection.CustomAttributeData> to discover information about custom attributes when you are working in the reflection-only context of an application domain.</span></span> <span data-ttu-id="56225-125"><xref:System.Reflection.CustomAttributeData> 可讓您檢查屬性而不需建立它們的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56225-125"><xref:System.Reflection.CustomAttributeData> allows you to examine attributes without creating instances of them.</span></span>  
  
 <span data-ttu-id="56225-126"><xref:System.Reflection.Emit> 命名空間的類別提供一種特殊形式的反映，可讓您在執行階段建置類型。</span><span class="sxs-lookup"><span data-stu-id="56225-126">The classes of the <xref:System.Reflection.Emit> namespace provide a specialized form of reflection that enables you to build types at run time.</span></span>  
  
 <span data-ttu-id="56225-127">反映也可以用來建立稱為類型瀏覽器的應用程式，可讓使用者選取類型，然後檢視這些類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="56225-127">Reflection can also be used to create applications called type browsers, which enable users to select types and then view the information about those types.</span></span>  
  
 <span data-ttu-id="56225-128">反映還有其他用途。</span><span class="sxs-lookup"><span data-stu-id="56225-128">There are other uses for reflection.</span></span> <span data-ttu-id="56225-129">JScript 之類的語言編譯器會使用反映來建構符號表。</span><span class="sxs-lookup"><span data-stu-id="56225-129">Compilers for languages such as JScript use reflection to construct symbol tables.</span></span> <span data-ttu-id="56225-130"><xref:System.Runtime.Serialization> 命名空間中的類別會使用反映來存取資料，並決定要保存哪個欄位。</span><span class="sxs-lookup"><span data-stu-id="56225-130">The classes in the <xref:System.Runtime.Serialization> namespace use reflection to access data and to determine which fields to persist.</span></span> <span data-ttu-id="56225-131"><xref:System.Runtime.Remoting> 命名空間中的類別在序列化時會間接使用反映。</span><span class="sxs-lookup"><span data-stu-id="56225-131">The classes in the <xref:System.Runtime.Remoting> namespace use reflection indirectly through serialization.</span></span>  
  
## <a name="runtime-types-in-reflection"></a><span data-ttu-id="56225-132">反映中的執行階段類型</span><span class="sxs-lookup"><span data-stu-id="56225-132">Runtime Types in Reflection</span></span>  
 <span data-ttu-id="56225-133">反映會提供類別，例如 <xref:System.Type> 和 <xref:System.Reflection.MethodInfo>，表示類型、成員、參數和其他程式碼實體。</span><span class="sxs-lookup"><span data-stu-id="56225-133">Reflection provides classes, such as <xref:System.Type> and <xref:System.Reflection.MethodInfo>, to represent types, members, parameters, and other code entities.</span></span> <span data-ttu-id="56225-134">不過，當您使用反映時不直接搭配類別使用，則其中大部分都會是抽象的 (在 Visual Basic 中為 `MustInherit`)。</span><span class="sxs-lookup"><span data-stu-id="56225-134">However, when you use reflection you don't work directly with these classes, most of which are abstract (`MustInherit` in Visual Basic).</span></span> <span data-ttu-id="56225-135">您可改用 Common Language Runtime (CLR) 所提供的類型。</span><span class="sxs-lookup"><span data-stu-id="56225-135">Instead, you work with types provided by the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="56225-136">例如，當您使用 C# `typeof` 運算子 (在 Visual Basic 中為 `GetType`) 來取得 <xref:System.Type> 物件時，該物件確實為 `RuntimeType`。</span><span class="sxs-lookup"><span data-stu-id="56225-136">For example, when you use the C# `typeof` operator (`GetType` in Visual Basic) to obtain a <xref:System.Type> object, the object is really a `RuntimeType`.</span></span> <span data-ttu-id="56225-137">`RuntimeType` 衍生自 <xref:System.Type>，並提供所有抽象方法的實作。</span><span class="sxs-lookup"><span data-stu-id="56225-137">`RuntimeType` derives from <xref:System.Type>, and provides implementations of all the abstract methods.</span></span>  
  
 <span data-ttu-id="56225-138">這些執行階段類別是 `internal` (在 Visual Basic 中為 `Friend`)。</span><span class="sxs-lookup"><span data-stu-id="56225-138">These runtime classes are `internal` (`Friend` in Visual Basic).</span></span> <span data-ttu-id="56225-139">它們不會分別從其基底類別記錄，因為它們的行為由基底類別的文件所描述。</span><span class="sxs-lookup"><span data-stu-id="56225-139">They are not documented separately from their base classes, because their behavior is described by the base class documentation.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="56225-140">相關主題</span><span class="sxs-lookup"><span data-stu-id="56225-140">Related Topics</span></span>  
  
|<span data-ttu-id="56225-141">標題</span><span class="sxs-lookup"><span data-stu-id="56225-141">Title</span></span>|<span data-ttu-id="56225-142">說明</span><span class="sxs-lookup"><span data-stu-id="56225-142">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="56225-143">檢視類型資訊</span><span class="sxs-lookup"><span data-stu-id="56225-143">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|<span data-ttu-id="56225-144">描述 <xref:System.Type> 類別，並提供程式碼範例說明如何搭配幾個反映類別來使用 <xref:System.Type>，以取得建構函式、方法、欄位、屬性和事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="56225-144">Describes the <xref:System.Type> class and provides code examples that illustrate how to use <xref:System.Type> with several reflection classes to obtain information about constructors, methods, fields, properties, and events.</span></span>|  
|[<span data-ttu-id="56225-145">反映和泛用類型</span><span class="sxs-lookup"><span data-stu-id="56225-145">Reflection and Generic Types</span></span>](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|<span data-ttu-id="56225-146">說明反映如何處理泛型類型和泛型方法的型別參數和型別引數。</span><span class="sxs-lookup"><span data-stu-id="56225-146">Explains how reflection handles the type parameters and type arguments of generic types and generic methods.</span></span>|  
|[<span data-ttu-id="56225-147">反映的安全性考量</span><span class="sxs-lookup"><span data-stu-id="56225-147">Security Considerations for Reflection</span></span>](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|<span data-ttu-id="56225-148">描述判斷可使用哪種程度的反映之規則，以探索類型資訊和存取類型。</span><span class="sxs-lookup"><span data-stu-id="56225-148">Describes the rules that determine to what degree reflection can be used to discover type information and access types.</span></span>|  
|[<span data-ttu-id="56225-149">動態載入和使用類型</span><span class="sxs-lookup"><span data-stu-id="56225-149">Dynamically Loading and Using Types</span></span>](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|<span data-ttu-id="56225-150">描述支援晚期繫結的反映自訂繫結介面。</span><span class="sxs-lookup"><span data-stu-id="56225-150">Describes the reflection custom-binding interface that supports late binding.</span></span>|  
|[<span data-ttu-id="56225-151">操作說明：將組件載入僅限反映的內容</span><span class="sxs-lookup"><span data-stu-id="56225-151">How to: Load Assemblies into the Reflection-Only Context</span></span>](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|<span data-ttu-id="56225-152">描述僅限反映的載入內容。</span><span class="sxs-lookup"><span data-stu-id="56225-152">Describes the reflection-only load context.</span></span> <span data-ttu-id="56225-153">示範如何載入組件、如何測試內容，以及如何檢查套用至僅限反映的內容中組件的屬性。</span><span class="sxs-lookup"><span data-stu-id="56225-153">Shows how to load an assembly, how to test the context, and how to examine attributes applied to an assembly in the reflection-only context.</span></span>|  
|[<span data-ttu-id="56225-154">存取自訂屬性</span><span class="sxs-lookup"><span data-stu-id="56225-154">Accessing Custom Attributes</span></span>](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|<span data-ttu-id="56225-155">示範如何使用反映來查詢屬性是否存在和屬性的值。</span><span class="sxs-lookup"><span data-stu-id="56225-155">Demonstrates using reflection to query attribute existence and values.</span></span>|  
|[<span data-ttu-id="56225-156">指定完整的類型名稱</span><span class="sxs-lookup"><span data-stu-id="56225-156">Specifying Fully Qualified Type Names</span></span>](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|<span data-ttu-id="56225-157">描述完整的類型名稱之格式，根據巴克斯格式 (BNF)，以及指定特殊字元、組件名稱、指標、參考和陣列所需的語法來描述。</span><span class="sxs-lookup"><span data-stu-id="56225-157">Describes the format of fully qualified type names in terms of the Backus-Naur form (BNF), and the syntax required for specifying special characters, assembly names, pointers, references, and arrays.</span></span>|  
|[<span data-ttu-id="56225-158">如何：使用反映連結委派</span><span class="sxs-lookup"><span data-stu-id="56225-158">How to: Hook Up a Delegate Using Reflection</span></span>](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|<span data-ttu-id="56225-159">說明如何建立方法的委派，以及連結委派到事件。</span><span class="sxs-lookup"><span data-stu-id="56225-159">Explains how to create a delegate for a method and hook the delegate up to an event.</span></span> <span data-ttu-id="56225-160">說明如何在執行階段使用 <xref:System.Reflection.Emit.DynamicMethod> 建立事件處理方法。</span><span class="sxs-lookup"><span data-stu-id="56225-160">Explains how to create an event-handling method at run time using <xref:System.Reflection.Emit.DynamicMethod>.</span></span>|  
|[<span data-ttu-id="56225-161">發出動態方法和組件</span><span class="sxs-lookup"><span data-stu-id="56225-161">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|<span data-ttu-id="56225-162">說明如何產生動態組件和動態方法。</span><span class="sxs-lookup"><span data-stu-id="56225-162">Explains how to generate dynamic assemblies and dynamic methods.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="56225-163">參考資料</span><span class="sxs-lookup"><span data-stu-id="56225-163">Reference</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
