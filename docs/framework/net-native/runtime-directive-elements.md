---
title: 執行階段指示詞項目
ms.date: 03/30/2017
ms.assetid: 3fe5848c-ecd7-4136-970b-8e48d250bde6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf692ff93a575858d1d1a89346611cb9c5957b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867039"
---
# <a name="runtime-directive-elements"></a>執行階段指示詞項目
執行階段指示詞 (rd.xml) 檔案格式支援下列執行階段指示詞元素。 如需階層表示法，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。  
  
 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md)  
 將執行階段反映原則套用至應用程式使用的所有類型，並做為整個應用程式的類型和類型成員的容器，這些類型和類型成員的中繼資料可在執行階段用於反映。 這是 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md) 項目的子項。  
  
 [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)  
 將執行階段原則套用至組件中的所有類型。 這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。  
  
 [\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)  
 如果其包含 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 指示詞是屬性，則會將執行階段原則套用至套用該屬性的程式碼項目。  
  
 [\<Directives>](../../../docs/framework/net-native/directives-element-net-native.md)  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 每個執行階段指示詞檔案中的根元素。 其子項目是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md)。  
  
 [\<Event>](../../../docs/framework/net-native/event-element-net-native.md)  
 將執行階段原則套用至事件。 這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。  
  
 [\<Field>](../../../docs/framework/net-native/field-element-net-native.md)  
 將執行階段原則套用至欄位。 這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。  
  
 [\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)  
 將執行階段原則套用至泛型類型或方法的參數類型。  
  
 [\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)  
 如果執行階段原則已套用至包含類型或方法，則會將該原則套用至類型。  
  
 [\<程式庫>](../../../docs/framework/net-native/library-element-net-native.md)  
 將執行階段原則套用至組件中的所有類型。 這是 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 和 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目的子項。  
  
 [\<Method>](../../../docs/framework/net-native/method-element-net-native.md)  
 將執行階段原則套用至方法。 這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。  
  
 [\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)  
 將執行階段原則套用至建構的泛型方法。 這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。  
  
 [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)  
 將執行階段原則套用至命名空間中的所有類型。  
  
 [\<Parameter>](../../../docs/framework/net-native/parameter-element-net-native.md)  
 將執行階段原則套用至傳遞給方法的引數類型。  
  
 [\<Property>](../../../docs/framework/net-native/property-element-net-native.md)  
 將執行階段原則套用至屬性。 這是 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 和 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 項目的子項。  
  
 [\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)  
 將執行階段原則套用至從包含類型繼承的所有類別。  
  
 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md)  
 將執行階段原則套用至類型。  
  
 [\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)  
 將執行階段原則套用至建構的泛型類型。  
  
 [\<TypeParameter>](../../../docs/framework/net-native/typeparameter-element-net-native.md)  
 將執行階段原則套用至傳遞給方法之 <xref:System.Type> 引數所表示的類型。  
  
## <a name="see-also"></a>另請參閱

- [rd.xml 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
