---
title: "依賴反映的 API"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49ac12bcae3fd85744961a6e3b81129178c2c323
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="apis-that-rely-on-reflection"></a>依賴反映的 API
在某些情況下，很難察覺程式碼中是否有使用反映，因此 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈不會保留執行階段所需的中繼資料。 本主題涵蓋一些常見的 API 或常見的程式設計模式，這些 API 或程式設計模式不是反映 API 的一部分，但依賴反映才能順利執行。 如果您在原始程式碼中使用這些 API 或程式設計模式，您可以將相關資訊加入至執行階段指示詞 (.rd.xml) 檔案，讓這些 API 的呼叫不會在執行階段擲回 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況或某個其他例外狀況。  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType 方法  
 您可以使用類似如下的程式碼呼叫 `AppClass<T>` 方法，以動態具現化泛型類型 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>：  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 若要在執行階段成功執行這個程式碼，需要幾個中繼資料項目。 第一個項目是未具現化之泛型類型 `Browse` 的 `AppClass<T>` 中繼資料：  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 這個中繼資料可成功呼叫 <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 方法，並傳回有效的 <xref:System.Type> 物件。  
  
 但是即使您加入未具現化之泛型型別的中繼資料，呼叫 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法還是會擲回 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況：  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 您可以將下列執行階段指示詞加入至執行階段指示詞檔案，以加入 `Activate` 中繼資料，對 `AppClass<T>` 的 <xref:System.Int32?displayProperty=nameWithType> 進行特定具現化：  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 如果 `AppClass<T>` 是使用 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 方法建立，並且不是以靜態方式使用，則對其進行之每個不同的具現化都需要個別的指示詞。  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod 方法  
 假設類別 `Class1` 具有泛型方法 `GetMethod<T>(T t)`，則可以使用類似如下的程式碼透過反映叫用 `GetMethod`：  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 若要成功執行，這個程式碼需要幾個中繼資料項目：  
  
-   您要呼叫其方法之類型的 `Browse` 中繼資料。  
  
-   您要呼叫方法的 `Browse` 中繼資料。  如果這是公用方法，加入包含類型的公用 `Browse` 中繼資料也會包含這個方法。  
  
-   您要呼叫之方法的動態中繼資料，如此一來，[!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈便不會移除反映引動過程委派。 如果方法遺漏動態中繼資料，呼叫 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 方法時會擲回下列例外狀況：  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 下列執行階段指示詞可確保提供所有必要的中繼資料：  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 動態叫用之方法的每個不同具現化各需要一個 `MethodInstantiation` 指示詞，並會更新 `Arguments` 元素以反映每個不同的具現化引數。  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array.CreateInstance 和 Type.MakeTypeArray 方法  
 下列範例會在 <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 類型上呼叫 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 和 `Class1` 方法。  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 如果沒有陣列中繼資料，則會產生下列錯誤：  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 需要陣列類型的 `Browse` 中繼資料，才能動態具現化陣列。  下列執行階段指示詞可動態具現化 `Class1[]`。  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>請參閱  
 [快速入門](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
