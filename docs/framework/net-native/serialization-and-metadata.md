---
title: 序列化和中繼資料
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c82d32fe5b1e62a19ff5e2920c5943f1303b2d64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207026"
---
# <a name="serialization-and-metadata"></a>序列化和中繼資料
如果您的應用程式將物件序列化和還原序列化，您可能需要將項目加入至執行階段指示詞 (.rd.xml) 檔案，以確保執行階段有必要的中繼資料存在。 有兩種類別的序列化程式，在執行階段指示詞檔案中，各需要不同的處理：  
  
-   反映型協力廠商序列化程式。 這些序列化程式需要修改您的執行階段指示詞檔案，將在下一節中討論。  
  
-   您可以在 .NET Framework 類別庫中找到非反映型序列化程式。 這些序列化程式可能需要修改您的執行階段指示詞檔案，將在 [Microsoft 序列化程式](#Microsoft)一節中討論。  
  
<a name="ThirdParty"></a>   
## <a name="third-party-serializers"></a>協力廠商序列化程式  
 協力廠商序列化程式 (包括 Newtonsoft.JSON) 通常是反映型。 若指定序列化資料的二進位大型物件 (BLOB)，將會依名稱查閱目標類型的欄位，以將資料中的欄位指派給具象類型。 針對您嘗試在 `List<Type>` 集合中序列化或還原序列化的每個 <xref:System.Type> 物件，使用這些程式庫至少會導致 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況。  
  
 若要為這些序列化程式解決因遺失中繼資料而導致的問題，最簡單的方法，就是收集要在單一命名空間 (例如 `App.Models`) 之下用於序列化的類型，並套用 `Serialize` 中繼資料指示詞：  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 如需範例中所使用語法的資訊，請參閱 [\<Namespace> 項目](../../../docs/framework/net-native/namespace-element-net-native.md)。  
  
<a name="Microsoft"></a>   
## <a name="microsoft-serializers"></a>Microsoft 序列化程式  
 雖然 <xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 和 <xref:System.Xml.Serialization.XmlSerializer> 類別不會依賴反映，但確實需要根據所要序列化或還原序列化的物件來產生程式碼。 適用於每個序列化程式的多載建構函式，包括用來指定要序列化或還原序列化之類型的 <xref:System.Type> 參數。 您用來將該類型指定在程式碼中的方式，會定義您必須採取的動作，在下兩節中將進行討論。  
  
### <a name="typeof-used-in-the-constructor"></a>用於建構函式的 typeof  
 如果您呼叫這些序列化類別的建構函式，並將 C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) 關鍵字包含在方法呼叫中，**就不需要執行任何額外的工作**。 例如，在對序列化類別建構函式進行的下列每個呼叫中，`typeof` 關鍵字會用來做為傳遞至建構函式之運算式的一部分。  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器將會自動處理這個程式碼。  
  
### <a name="typeof-used-outside-the-constructor"></a>在建構函式外部使用的 typeof  
 如果您呼叫這些序列化類別的建構函式，並且在提供給建構函式之 <xref:System.Type> 參數的運算式外部，使用 C# [typeof](~/docs/csharp/language-reference/keywords/typeof.md) 關鍵字 (如下列程式碼所示)，則 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器無法解析類型：  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 在此情況下，您必須加入像下列這樣的項目，以在執行階段指示詞檔案中指定類型：  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 同樣地，如果您呼叫 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> 之類的建構函式，並提供要序列化的其他 <xref:System.Type> 物件陣列 (如下列程式碼)，則 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 編譯器無法解析這些類型。  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 您必須針對每一種類型，在執行階段指示詞檔案中加入像下列的項目：  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 如需範例中所使用語法的資訊，請參閱 [\<Type> 項目](../../../docs/framework/net-native/type-element-net-native.md)。  
  
## <a name="see-also"></a>另請參閱

- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞項目](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<型別 > 項目](../../../docs/framework/net-native/type-element-net-native.md)
- [\<命名空間 > 項目](../../../docs/framework/net-native/namespace-element-net-native.md)
