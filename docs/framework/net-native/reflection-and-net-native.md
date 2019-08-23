---
title: 反映和 .NET Native
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8594d29aab7f07dce150671493bbf70f9832fb44
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935164"
---
# <a name="reflection-and-net-native"></a>反映和 .NET Native
在 .NET Framework 中，Managed 開發可透過反映 API 來支援 metaprogramming。 反映可讓您檢查應用程式中的物件、在透過檢查發現的物件上呼叫方法、在執行階段產生新的類型，並可支援許多其他動態程式碼案例。 它也支援序列化和還原序列化，可讓物件的欄位值保存下來，並於稍後還原。 這些案例全都需要 .NET Framework just-in-time (JIT) 編譯器依據可用的中繼資料來產生機器碼。  
  
 .NET Native 執行時間不包含 JIT 編譯程式。 因此，必須事先產生所有必要的機器碼。 系統會使用一組啟發學習法來判斷應該產生哪些程式碼，但這些啟發學習法無法涵蓋所有可能的 metaprogramming 案例。  因此，您必須使用[執行階段指示詞](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)，提供提示給這些 metaprogramming 案例。 如果在執行階段時未提供必要的中繼資料或實作程式碼，則應用程式會擲回 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 或 [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 例外狀況。 您可以使用兩個疑難排解工具，這些工具會產生可讓執行階段指示詞檔案消除例外狀況的適當項目：  
  
- 針對類型的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/type.html) 。  
  
- 針對方法的 [MissingMetadataException 疑難排解工具](https://dotnet.github.io/native/troubleshooter/method.html) 。  
  
> [!NOTE]
> 如需 .NET 原生編譯程序的概觀 (其提供需要執行階段指示詞檔案的背景資訊)，請參閱 [.NET 原生和編譯](../../../docs/framework/net-native/net-native-and-compilation.md)。  
  
 此外, .NET Native 不允許您反映 .NET Framework Class Library 的私用成員。 例如，呼叫 <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> 屬性來擷取 .NET Framework 類別庫類型，只會傳回公用或受保護的欄位。  
  
 下列主題提供您在應用程式中支援反映和序列化時，所需的概念和參考文件：  
  
- [依賴反映的 API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
- [反映 API 參考](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
- [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>另請參閱

- [使用 .NET Native 編譯應用程式](../../../docs/framework/net-native/index.md)
- [.NET Native 和編譯](../../../docs/framework/net-native/net-native-and-compilation.md)
