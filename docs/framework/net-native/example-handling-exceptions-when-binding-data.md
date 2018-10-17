---
title: 範例：處理繫結資料時所發生的例外狀況
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a861da011898c3648c66b6a0ea0f97cdb26ff288
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374023"
---
# <a name="example-handling-exceptions-when-binding-data"></a>範例：處理繫結資料時所發生的例外狀況
> [!NOTE]
>  本主題討論 .NET 原生開發人員預覽，這是發行前版本的軟體。 您可以從 [Microsoft Connect 網站](https://go.microsoft.com/fwlink/?LinkId=394611)下載預覽 (需要註冊)。  
  
 下列範例顯示如何解決當以 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈編譯的應用程式嘗試繫結資料時，所擲回的 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況。 以下是例外狀況資訊：  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 以下是相關聯的呼叫堆疊：  
  
```  
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f   
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31   
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>應用程式做了什麼？  
 在堆疊的基底，框架<xref:Windows.UI.Xaml?displayProperty=nameWithType>命名空間可讓您指出 XAML 轉譯引擎正在執行。   使用 <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> 方法會指出，在已移除中繼資料的類型上，以反映方式查閱屬性的值。  
  
 提供中繼資料指示詞的第一個步驟，就是為該類型加入 `serialize` 中繼資料，讓它的所有屬性皆可供存取：  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>這是個案嗎？  
 在這個案例中，如果資料繫結中有一個 `ViewModel` 的中繼資料不完整，其他的可能也一樣。  如果程式碼的結構化方式是應用程式的檢視模型全都在 `App.ViewModels` 命名空間中，您可以使用較為普遍的執行階段指示詞：  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>可以將程式碼改寫為不使用反映嗎？  
 因為資料繫結是是反映密集作業，所以變更程式碼來避免反映並不可行。  
  
 不過，有一些方法可以將 `ViewModel` 指定至 XAML 頁面，讓工具鏈可以在編譯時將屬性繫結與正確的類型建立關聯，並且在不使用執行階段指示詞的情況下保留中繼資料。  例如，您可以套用<xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType>屬性上的屬性。 這會導致 XAML 編譯器產生必要的查閱資訊，並避免 Default.rd.xml 檔案中需要執行階段指示詞。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [範例：針對動態程式設計進行疑難排解](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
