---
title: MissingRuntimeArtifactException 類別 (.NET Native)
ms.date: 03/30/2017
ms.assetid: d5b3d13e-689f-4584-8ba6-44f5167a8590
ms.openlocfilehash: 2618af8e122964d64126f945c337101cb5bbe5ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250901"
---
# <a name="missingruntimeartifactexception-class-net-native"></a>MissingRuntimeArtifactException 類別 (.NET Native)

**適用于 Windows 應用程式的 .NET Windows 10，僅 .NET Native**  
  
 當類型或類型成員的中繼資料可用，但已移除其實作時，會擲回這個例外狀況。  
  
 **命名空間：** System.Reflection  
  
> [!IMPORTANT]
> 類別僅供 `MissingRuntimeArtifactException` .NET Native 工具鏈內部使用。 這主要並非用於協力廠商程式碼中，也不應該在應用程式程式碼中處理此例外狀況。 相反地，請藉由將項目新增至[執行階段指示詞檔案](runtime-directives-rd-xml-configuration-file-reference.md)，來消除例外狀況。 如需詳細資訊，請參閱＜備註＞一節。  
  
## <a name="syntax"></a>Syntax  

 [!code-csharp[ProjectN#22](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingruntimeartifactexception_syntax1.cs#22)]  
  
 請注意，`MissingRuntimeArtifactException` 類別衍生自 <xref:System.MemberAccessException>。  
  
 `MissingRuntimeArtifactException` 類別具有下列成員：  
  
## <a name="constructors"></a>建構函式  
  
|建構函式|描述|  
|-----------------|-----------------|  
|`public MissingRuntimeArtifactException()`|使用系統提供的錯誤說明訊息，初始化 `MissingRuntimeArtifactException` 類別的新執行個體。<br /><br /> 這個函式僅供 .NET Native 工具鏈內部使用。|  
|`public MissingRuntimeArtifactException(String message)`|使用指定的錯誤訊息，初始化 `MissingRuntimeArtifactException` 類別的新執行個體。<br /><br /> 這個函式僅供 .NET Native 工具鏈內部使用。|  
  
## <a name="properties"></a>屬性  
  
|屬性|描述|  
|--------------|-----------------|  
|`public IDictionary Data { get; }`|取得鍵值組的集合，這些鍵值組會提供關於例外狀況的其他使用者定義資訊。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public string HelpLink { get; set; }`|取得或設定與這個例外狀況相關聯的說明檔連結。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public int HResult { get; protected set; }`|取得或設定 `HRESULT`，這是指派給特定例外狀況的編碼數值。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public Exception InnerException { get; }`|取得造成目前例外狀況的例外狀況。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public string Message { get; }`|取得描述目前例外狀況的訊息。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public string Source { get; set; }`|取得或設定造成錯誤的應用程式或物件名稱。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public string StackTrace { get; }`|取得呼叫堆疊上即時運算框架的字串表示。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public MethodBase TargetSite { get; }`|取得擲回目前例外狀況的方法。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|`public bool Equals(Object obj)`|判斷指定的物件是否等於目前的物件。  (繼承自 <xref:System.Object>。)|  
|`protected void Finalize()`|允許物件在記憶體回收進行回收之前，嘗試釋放資源並執行其他清除作業。 (繼承自 <xref:System.Object>。)|  
|`public Exception GetBaseException()`|傳回一或多個後續例外狀況之根本原因的例外狀況。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public int GetHashCode()`|傳回 `MissingRuntimeArtifactException` 執行個體的雜湊碼。   (繼承自 <xref:System.Object>。)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|使用例外狀況的相關資訊來設定 <xref:System.Runtime.Serialization.SerializationInfo> 物件。  (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`public Type GetType()`|取得目前執行個體的執行階段類型。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
|`protected Object MemberwiseClone()`|建立目前物件的淺層複本。 (繼承自 <xref:System.Object>。)|  
|`public string ToString()`|傳回目前例外狀況的字串表示。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
  
## <a name="events"></a>事件  
  
|事件|描述|  
|-----------|-----------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|當例外狀況序列化，以建立包含例外狀況相關序列化資料的例外狀況狀態物件時，就會發生此事件。 (繼承自 <xref:System.Exception?displayProperty=nameWithType>。)|  
  
## <a name="usage-details"></a>使用量詳細資料  

 當嘗試具現化類型或叫用類型成員時，雖然存在該類型或成員的中繼資料，但已移除其實作，在此情況下會擲回 `MissingRuntimeArtifactException` 例外狀況。  
  
 應用程式在執行時間是否可透過執行時間指示詞，以動態方式執行方法的中繼資料和執行程式碼，是由執行時間指示詞所定義 (XML 設定) 檔 \*.rd.xml。 若要防止應用程式擲回這個例外狀況，您必須修改 \*.rd.xml，以確保在執行階段存在類型或類型成員所需的中繼資料。 如需 \*.rd.xml 檔案格式的資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)。  
  
> [!IMPORTANT]
> 因為這個例外狀況指出應用程式所需的實作程式碼在執行階段無法使用，所以您不應該在 `try`/`catch` 區塊中處理這個例外狀況。 相反地，您應該診斷例外狀況的原因，然後透過執行階段指示詞檔案來去除這個例外狀況。 一般來說，您可以在執行時間指示詞檔案 `Activate` 中為程式元素指定適當或 `Dynamic` 原則， (.rd.xml 檔) 來消除這個例外狀況 \* 。 若要取得可加入執行階段指示詞檔案以消除例外狀況的項目，您可以使用下列兩個疑難排解工具之一：  
>
> - 針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。  
> - 針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。  
  
 `MissingRuntimeArtifactException` 類別沒有包含唯一成員；其所有成員都是繼承自其基底類別 <xref:System.MemberAccessException>。  
  
## <a name="see-also"></a>另請參閱

- [執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)
- [執行階段指示詞原則設定](runtime-directive-policy-settings.md)
