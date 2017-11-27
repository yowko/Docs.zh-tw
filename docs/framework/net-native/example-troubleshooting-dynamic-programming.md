---
title: "範例：動態程式設計疑難排解"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de808e333506858d6591dab6c7c06e6a3e9ddabd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="example-troubleshooting-dynamic-programming"></a>範例：動態程式設計疑難排解
> [!NOTE]
>  本主題討論 .NET 原生開發人員預覽，這是發行前版本的軟體。 您可以從 [Microsoft Connect 網站](http://go.microsoft.com/fwlink/?LinkId=394611)下載預覽 (需要註冊)。  
  
 在使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈開發的應用程式中，並非所有的中繼資料查閱失敗都會導致例外狀況。  有些中繼資料查閱失敗會在應用程式中以無法預期的方式顯露出來。  下列範例顯示因為參考 null 物件而造成的存取違規：  
  
```  
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 讓我們試著使用[使用者入門](../../../docs/framework/net-native/getting-started-with-net-native.md)的＜手動解析遺失的中繼資料＞一節中描述的三步驟方法，針對這個例外狀況進行疑難排解。  
  
## <a name="what-was-the-app-doing"></a>應用程式做了什麼？  
 要注意的第一件事，就是位於堆疊基底的 `async` 關鍵字裝置。  判斷應用程式在 `async` 方法中真正做了什麼可能會有問題，因為堆疊已失去原始呼叫的內容，而且已經在不同的執行緒上執行 `async` 程式碼。 不過，我們可以推算應用程式是在嘗試載入其第一個分頁。  在 `NavigationArgs.Setup` 的實作中，下列程式碼造成了存取違規：  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 在這個範例中，`AppViewModel.Current` 上的 `LayoutVM` 屬性為 **null**。  因為缺少某些中繼資料，而造成細微的行為差異，並導致解除初始化屬性，而不是依照應用程式預期來設定屬性。  在應該已初始化 `LayoutVM` 的程式碼中設定中斷點，也許可以釐清這個情況。  不過，請注意，`LayoutVM` 的類型是 `App.Core.ViewModels.Layout.LayoutApplicationVM`。  目前為止，rd.xml 檔案中唯一存在的中繼資料指示詞是：  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 可能的失敗原因，就是 `App.Core.ViewModels.Layout.LayoutApplicationVM` 遺失中繼資料，因為它是在不同的命名空間中。  
  
 在此情況下，為 `App.Core.ViewModels` 加入執行階段指示詞就解決了問題。 根本原因是對 <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> 方法進行的 API 呼叫傳回 **null**，而應用程式靜靜忽略這個問題，直到發生當機。  
  
 在動態程式設計中，在 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 之下使用反映 API 的好作法，是使用會在失敗時擲回例外狀況的 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 多載。  
  
## <a name="is-this-an-isolated-case"></a>這是個案嗎？  
 使用 `App.Core.ViewModels` 時，可能也會發生其他問題。  您必須決定是否值得識別並修正每個遺失中繼資料的例外狀況，還是要節省時間，並為較大類別的類型加入指示詞。  在這裡，如果輸出二進位檔產生的結果大小增加並不是問題，則為 `dynamic` 加入 `App.Core.ViewModels` 中繼資料可能是最佳方法。  
  
## <a name="could-the-code-be-rewritten"></a>可以改寫程式碼嗎？  
 如果應用程式使用 `typeof(LayoutApplicationVM)`，而不是 `Type.GetType("LayoutApplicationVM")`，則工具鏈可能保留了 `browse` 中繼資料。  不過，它還是不會建立 `invoke` 中繼資料，如此一來，在具現化類型時，就會導致 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況。 若要避免這個例外狀況，您還是必須為命名空間或是指定 `dynamic` 原則的類型加入執行階段指示詞。 如需執行階段指示詞的相關資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [範例：處理繫結資料時所發生的例外狀況](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
