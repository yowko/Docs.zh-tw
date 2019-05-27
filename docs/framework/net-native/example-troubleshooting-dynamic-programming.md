---
title: 範例：針對動態程式設計進行疑難排解
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e482303e684813574a092f0a2d5812445ed7fa6e
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052610"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="7b084-102">範例：針對動態程式設計進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="7b084-102">Example: Troubleshooting Dynamic Programming</span></span>
> [!NOTE]
>  <span data-ttu-id="7b084-103">本主題討論 .NET 原生開發人員預覽，這是發行前版本的軟體。</span><span class="sxs-lookup"><span data-stu-id="7b084-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="7b084-104">您可以從 [Microsoft Connect 網站](https://go.microsoft.com/fwlink/?LinkId=394611)下載預覽 (需要註冊)。</span><span class="sxs-lookup"><span data-stu-id="7b084-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="7b084-105">並非所有的中繼資料查閱失敗，應用程式中開發使用.NET Native 工具鏈結果的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7b084-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="7b084-106">有些中繼資料查閱失敗會在應用程式中以無法預期的方式顯露出來。</span><span class="sxs-lookup"><span data-stu-id="7b084-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="7b084-107">下列範例顯示因為參考 null 物件而造成的存取違規：</span><span class="sxs-lookup"><span data-stu-id="7b084-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
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
  
 <span data-ttu-id="7b084-108">讓我們試著使用[使用者入門](../../../docs/framework/net-native/getting-started-with-net-native.md)的＜手動解析遺失的中繼資料＞一節中描述的三步驟方法，針對這個例外狀況進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="7b084-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="7b084-109">應用程式做了什麼？</span><span class="sxs-lookup"><span data-stu-id="7b084-109">What was the app doing?</span></span>  
 <span data-ttu-id="7b084-110">要注意的第一件事，就是位於堆疊基底的 `async` 關鍵字裝置。</span><span class="sxs-lookup"><span data-stu-id="7b084-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="7b084-111">判斷應用程式在 `async` 方法中真正做了什麼可能會有問題，因為堆疊已失去原始呼叫的內容，而且已經在不同的執行緒上執行 `async` 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b084-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="7b084-112">不過，我們可以推算應用程式是在嘗試載入其第一個分頁。</span><span class="sxs-lookup"><span data-stu-id="7b084-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="7b084-113">在 `NavigationArgs.Setup` 的實作中，下列程式碼造成了存取違規：</span><span class="sxs-lookup"><span data-stu-id="7b084-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
```  
AppViewModel.Current.LayoutVM.PageMap  
```  
  
 <span data-ttu-id="7b084-114">在這個範例中，`AppViewModel.Current` 上的 `LayoutVM` 屬性為 **null**。</span><span class="sxs-lookup"><span data-stu-id="7b084-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="7b084-115">因為缺少某些中繼資料，而造成細微的行為差異，並導致解除初始化屬性，而不是依照應用程式預期來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="7b084-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="7b084-116">在應該已初始化 `LayoutVM` 的程式碼中設定中斷點，也許可以釐清這個情況。</span><span class="sxs-lookup"><span data-stu-id="7b084-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="7b084-117">不過，請注意，`LayoutVM` 的類型是 `App.Core.ViewModels.Layout.LayoutApplicationVM`。</span><span class="sxs-lookup"><span data-stu-id="7b084-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="7b084-118">目前為止，rd.xml 檔案中唯一存在的中繼資料指示詞是：</span><span class="sxs-lookup"><span data-stu-id="7b084-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="7b084-119">可能的失敗原因，就是 `App.Core.ViewModels.Layout.LayoutApplicationVM` 遺失中繼資料，因為它是在不同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="7b084-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="7b084-120">在此情況下，為 `App.Core.ViewModels` 加入執行階段指示詞就解決了問題。</span><span class="sxs-lookup"><span data-stu-id="7b084-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="7b084-121">根本原因是對 <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> 方法進行的 API 呼叫傳回 **null**，而應用程式靜靜忽略這個問題，直到發生當機。</span><span class="sxs-lookup"><span data-stu-id="7b084-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="7b084-122">在動態程式設計中，使用反映 Api 在.NET 原生時最好是使用<xref:System.Type.GetType%2A?displayProperty=nameWithType>多載，可在失敗時擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7b084-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="7b084-123">這是個案嗎？</span><span class="sxs-lookup"><span data-stu-id="7b084-123">Is this an isolated case?</span></span>  
 <span data-ttu-id="7b084-124">使用 `App.Core.ViewModels` 時，可能也會發生其他問題。</span><span class="sxs-lookup"><span data-stu-id="7b084-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="7b084-125">您必須決定是否值得識別並修正每個遺失中繼資料的例外狀況，還是要節省時間，並為較大類別的類型加入指示詞。</span><span class="sxs-lookup"><span data-stu-id="7b084-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="7b084-126">在這裡，如果輸出二進位檔產生的結果大小增加並不是問題，則為 `dynamic` 加入 `App.Core.ViewModels` 中繼資料可能是最佳方法。</span><span class="sxs-lookup"><span data-stu-id="7b084-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="7b084-127">可以改寫程式碼嗎？</span><span class="sxs-lookup"><span data-stu-id="7b084-127">Could the code be rewritten?</span></span>  
 <span data-ttu-id="7b084-128">如果應用程式使用 `typeof(LayoutApplicationVM)`，而不是 `Type.GetType("LayoutApplicationVM")`，則工具鏈可能保留了 `browse` 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7b084-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="7b084-129">不過，它還是不會建立 `invoke` 中繼資料，如此一來，在具現化類型時，就會導致 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7b084-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="7b084-130">若要避免這個例外狀況，您還是必須為命名空間或是指定 `dynamic` 原則的類型加入執行階段指示詞。</span><span class="sxs-lookup"><span data-stu-id="7b084-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="7b084-131">如需執行階段指示詞的相關資訊，請參閱[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7b084-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b084-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b084-132">See also</span></span>

- [<span data-ttu-id="7b084-133">快速入門</span><span class="sxs-lookup"><span data-stu-id="7b084-133">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="7b084-134">例如：資料繫結時處理例外狀況</span><span class="sxs-lookup"><span data-stu-id="7b084-134">Example: Handling Exceptions When Binding Data</span></span>](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)
