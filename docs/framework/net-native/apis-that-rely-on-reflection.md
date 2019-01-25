---
title: 依賴反映的 API
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26a198db13e5855d9473cf7780dade9ce95e9298
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610836"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="058e2-102">依賴反映的 API</span><span class="sxs-lookup"><span data-stu-id="058e2-102">APIs That Rely on Reflection</span></span>
<span data-ttu-id="058e2-103">在某些情況下，很難察覺程式碼中是否有使用反映，因此 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈不會保留執行階段所需的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="058e2-103">In some cases, the use of reflection in code isn't obvious, and so the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="058e2-104">本主題涵蓋一些常見的 API 或常見的程式設計模式，這些 API 或程式設計模式不是反映 API 的一部分，但依賴反映才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="058e2-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="058e2-105">如果您在原始程式碼中使用這些 API 或程式設計模式，您可以將相關資訊加入至執行階段指示詞 (.rd.xml) 檔案，讓這些 API 的呼叫不會在執行階段擲回 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況或某個其他例外狀況。</span><span class="sxs-lookup"><span data-stu-id="058e2-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="058e2-106">Type.MakeGenericType 方法</span><span class="sxs-lookup"><span data-stu-id="058e2-106">Type.MakeGenericType method</span></span>  
 <span data-ttu-id="058e2-107">您可以使用類似如下的程式碼呼叫 `AppClass<T>` 方法，以動態具現化泛型類型 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="058e2-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="058e2-108">若要在執行階段成功執行這個程式碼，需要幾個中繼資料項目。</span><span class="sxs-lookup"><span data-stu-id="058e2-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="058e2-109">第一個項目是未具現化之泛型類型 `Browse` 的 `AppClass<T>` 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="058e2-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="058e2-110">這個中繼資料可成功呼叫 <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 方法，並傳回有效的 <xref:System.Type> 物件。</span><span class="sxs-lookup"><span data-stu-id="058e2-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="058e2-111">但是即使您加入未具現化之泛型型別的中繼資料，呼叫 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法還是會擲回 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況：</span><span class="sxs-lookup"><span data-stu-id="058e2-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 <span data-ttu-id="058e2-112">您可以將下列執行階段指示詞加入至執行階段指示詞檔案，以加入 `Activate` 中繼資料，對 `AppClass<T>` 的 <xref:System.Int32?displayProperty=nameWithType> 進行特定具現化：</span><span class="sxs-lookup"><span data-stu-id="058e2-112">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="058e2-113">如果 `AppClass<T>` 是使用 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法建立，並且不是以靜態方式使用，則對其進行之每個不同的具現化都需要個別的指示詞。</span><span class="sxs-lookup"><span data-stu-id="058e2-113">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="058e2-114">MethodInfo.MakeGenericMethod 方法</span><span class="sxs-lookup"><span data-stu-id="058e2-114">MethodInfo.MakeGenericMethod method</span></span>  
 <span data-ttu-id="058e2-115">假設類別 `Class1` 具有泛型方法 `GetMethod<T>(T t)`，則可以使用類似如下的程式碼透過反映叫用 `GetMethod`：</span><span class="sxs-lookup"><span data-stu-id="058e2-115">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="058e2-116">若要成功執行，這個程式碼需要幾個中繼資料項目：</span><span class="sxs-lookup"><span data-stu-id="058e2-116">To run successfully, this code requires several items of metadata:</span></span>  
  
-   <span data-ttu-id="058e2-117">您要呼叫其方法之類型的 `Browse` 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="058e2-117">`Browse` metadata for the type whose method you want to call.</span></span>  
  
-   <span data-ttu-id="058e2-118">您要呼叫方法的 `Browse` 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="058e2-118">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="058e2-119">如果這是公用方法，加入包含類型的公用 `Browse` 中繼資料也會包含這個方法。</span><span class="sxs-lookup"><span data-stu-id="058e2-119">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
-   <span data-ttu-id="058e2-120">您要呼叫之方法的動態中繼資料，如此一來，[!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈便不會移除反映引動過程委派。</span><span class="sxs-lookup"><span data-stu-id="058e2-120">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain.</span></span> <span data-ttu-id="058e2-121">如果方法遺漏動態中繼資料，呼叫 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 方法時會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="058e2-121">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="058e2-122">下列執行階段指示詞可確保提供所有必要的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="058e2-122">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="058e2-123">動態叫用之方法的每個不同具現化各需要一個 `MethodInstantiation` 指示詞，並會更新 `Arguments` 元素以反映每個不同的具現化引數。</span><span class="sxs-lookup"><span data-stu-id="058e2-123">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="058e2-124">Array.CreateInstance 和 Type.MakeTypeArray 方法</span><span class="sxs-lookup"><span data-stu-id="058e2-124">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  
 <span data-ttu-id="058e2-125">下列範例會在 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 類型上呼叫 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 和 `Class1` 方法。</span><span class="sxs-lookup"><span data-stu-id="058e2-125">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="058e2-126">如果沒有陣列中繼資料，則會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="058e2-126">If no array metadata is present, the following error results:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="058e2-127">需要陣列類型的 `Browse` 中繼資料，才能動態具現化陣列。</span><span class="sxs-lookup"><span data-stu-id="058e2-127">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="058e2-128">下列執行階段指示詞可動態具現化 `Class1[]`。</span><span class="sxs-lookup"><span data-stu-id="058e2-128">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="058e2-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="058e2-129">See also</span></span>
- [<span data-ttu-id="058e2-130">快速入門</span><span class="sxs-lookup"><span data-stu-id="058e2-130">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="058e2-131">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="058e2-131">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
