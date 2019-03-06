---
title: MissingMetadataException 類別 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2961a4c02d8ffe17055307094f56a03680d1a59a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357127"
---
# <a name="missingmetadataexception-class-net-native"></a>MissingMetadataException 類別 (.NET Native)

**僅限 Windows 10 之 Windows 應用程式的 .NET[!INCLUDE[net_native](../../../includes/net-native-md.md)]**

使用反映來擷取不存在的中繼資料時，所擲回的例外狀況。

**命名空間：** System.Reflection

> [!IMPORTANT]
> 
  `MissingMetadataException` 類別主要僅供　[!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈內部使用。 這主要並非用於協力廠商程式碼中，也不應該在應用程式程式碼中處理此例外狀況。 相反地，請藉由將項目新增至[執行階段指示詞檔案](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)，來消除例外狀況。 如需詳細資訊，請參閱＜備註＞一節。

## <a name="syntax"></a>語法

[!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]

請注意 `MissingMetadataException` 類別衍生自 <xref:System.TypeAccessException>。

`MissingMetadataException` 類別具有下列成員：

## <a name="constructors"></a>建構函式

|建構函式|描述|
|-----------------|-----------------|
|`public MissingMetadataException()`|使用系統提供的錯誤說明訊息，初始化 `MissingMetadataException` 類別的新執行個體。<br /><br /> 這個建構函式僅供 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈內部使用。|
|`public MissingMetadataException(String message)`|使用指定的錯誤訊息，初始化 `MissingMetadataException` 類別的新執行個體。<br /><br /> 這個建構函式僅供 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈內部使用。|

## <a name="properties"></a>屬性

|屬性|描述|
|--------------|-----------------|
|`public IDictionary Data { get; }`|取得提供例外狀況之其他使用者定義相關資訊的索引鍵/值組集合。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public string HelpLink { get; set; }`|取得或設定與這個例外狀況相關聯的說明檔連結。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public int HResult { get; protected set; }`|取得或設定 `HRESULT`，這是指派給特定例外狀況的編碼數值。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public Exception InnerException { get; }`|取得造成目前例外狀況的例外狀況。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public string Message { get; }`|取得描述目前例外狀況的訊息。 (繼承自 <xref:System.TypeLoadException>。)|
|`public string Source { get; set; }`|取得或設定造成錯誤的應用程式或物件名稱。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public string StackTrace { get; }`|取得呼叫堆疊上即時運算框架的字串表示。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public MethodBase TargetSite { get; }`|取得擲回目前例外狀況的方法。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public string TypeName { get; ]`|取得遺失中繼資料之類型的完整名稱。 (繼承自 <xref:System.TypeLoadException>。)|

## <a name="methods"></a>方法

|方法|描述|
|------------|-----------------|
|`public bool Equals(Object obj)`|判斷指定的物件是否等於目前的物件。  (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`protected void Finalize()`|在記憶體回收開始前，允許物件嘗試釋放資源，並執行其他清除作業。 (繼承自 <xref:System.Object>。)|
|`public Exception GetBaseException()`|傳回一或多個後續例外狀況之根本原因的例外狀況。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`public int GetHashCode()`|傳回 `MissingMetadataException` 執行個體的雜湊碼。   (繼承自 <xref:System.Object>。)|
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|使用與例外狀況相關的資訊來設定 <xref:System.Runtime.Serialization.SerializationInfo> 物件。  (繼承自 <xref:System.TypeLoadException>。)|
|`public Type GetType()`|取得目前執行個體的執行階段類型。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|
|`protected Object MemberwiseClone()`|建立目前物件的淺層複本。 (繼承自 <xref:System.Object>。)|
|`public string ToString()`|傳回目前例外狀況的字串表示。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|

## <a name="events"></a>事件

|Event - 事件|描述|
|-----------|-----------------|
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|當例外狀況序列化，以建立包含例外狀況相關序列化資料的例外狀況狀態物件時，就會發生此事件。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|

## <a name="usage-details"></a>用法詳細資料

使用反映來存取組件中沒有的中繼資料時，就會擲回 `MissingMetadataException` 例外狀況。

應用程式在執行階段是否有中繼資料可用，是由執行階段指示詞 (XML 組態) 檔案 *.rd.xml 所定義。 若要防止您的應用程式擲回這個例外狀況，您必須修改 \*.rd.xml，以定義必須出現在執行階段的中繼資料。 如需 \*.rd.xml 檔案格式的資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。

> [!IMPORTANT]
> 因為這個例外狀況指出應用程式所需的中繼資料在執行階段無法使用，所以您不應該在 `try`/`catch` 區塊中處理這個例外狀況。 相反地，您應該診斷例外狀況的原因，然後透過執行階段指示詞檔案來去除這個例外狀況。 若要取得可加入執行階段指示詞檔案以消除例外狀況的項目，您可以使用下列兩個疑難排解工具之一：
>
> - 針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。
> - 針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。


  `MissingMetadataException` 類別沒有包含唯一成員；其所有成員都是繼承自其基底類別 <xref:System.TypeAccessException>。

## <a name="see-also"></a>另請參閱

- <xref:System.Exception?displayProperty=nameWithType>
- <xref:System.TypeAccessException>
- [MissingInteropDataException 類別](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingRuntimeArtifactException 類別](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
