---
title: .NET 原生反映 API 參考
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35dcabcf65af1634533edfba1e300a8746bc97ec
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221364"
---
# <a name="net-native-reflection-api-reference"></a>.NET 原生反映 API 參考
[!INCLUDE[net_native](../../../includes/net-native-md.md)] 包含三個新的例外狀況類型：[System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)， [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)，以及[System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). 請注意有關下列三個例外狀況類型的資訊：  
  
 這些類型僅供內部使用。  
 這三個例外狀況類型僅供 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈使用。 當 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈偵測到不允許程式繼續執行的遺失資料時，會擲回例外狀況。  
  
 請勿在您的程式碼中處理這些例外狀況。  
 這些例外狀況表示應用程式所需的中繼資料不存在 ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 和 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況) 或應用程式所需的實作程式碼已遺失 ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外狀況)。 您可修改執行階段指示詞 (rd.xml) 檔案來修正這些例外狀況，以便在執行階段提供必要的中繼資料或實作程式碼。 如需詳細資訊，請參閱 [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。 有兩個疑難排解工具可用，這些工具為您的執行階段指示詞檔案提供適當的項目，將可排除 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 和 [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外狀況：  
  
-   針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。  
  
-   針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。  
  
> [!NOTE]
>  此參考文件記載 [!INCLUDE[net_native](../../../includes/net-native-md.md)]特有的三個例外狀況類型。 如需.NET Framework 核心反映 API 參考文件，請參閱 < <xref:System.Reflection>，<xref:System.Reflection.Context>和<xref:System.Reflection.Emit>命名空間。 如需 .NET Framework 核心 interop API 的參考文件，請參閱 <xref:System.Runtime.InteropServices>。  
  
## <a name="systemreflection-namespace"></a>System.Reflection 命名空間  
 <xref:System.Reflection> 命名空間包含用於在 .NET Framework 中反映的核心類型。 針對 [!INCLUDE[net_native](../../../includes/net-native-md.md)]，它還包含兩個新的例外狀況類型：  
  
|類別|描述|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|使用反映來擷取不存在的中繼資料時，所擲回的例外狀況。|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|當類型或類型成員的中繼資料可用，但已移除其實作時，會擲回這個例外狀況。|  
  
 如需有關這個命名空間中其他類型的說明文件，請參閱 .NET Framework 文件集中的 <xref:System.Reflection> 參考頁面。  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices 命名空間  
 <xref:System.Runtime.CompilerServices> 命名空間包含語言編譯器為使用者設計的類型。 針對 [!INCLUDE[net_native](../../../includes/net-native-md.md)]，它還包含一個新的例外狀況類型：  
  
|類別|描述|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|當呼叫手動封送處理方法，但靜態分析或執行階段指示詞檔案中找不到類型的中繼資料時，會擲回這個例外狀況。|  
  
 如需有關這個命名空間中其他類型的說明文件，請參閱 .NET Framework 文件集中的 <xref:System.Runtime.CompilerServices> 參考頁面。  
  
## <a name="see-also"></a>另請參閱
- [MissingInteropDataException 類別](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingMetadataException 類別](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException 類別](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [快速入門](../../../docs/framework/net-native/getting-started-with-net-native.md)
