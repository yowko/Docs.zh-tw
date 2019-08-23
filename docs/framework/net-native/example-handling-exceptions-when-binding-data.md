---
title: 範例：處理繫結資料時所發生的例外狀況
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5be728cbeb0c3378bb35765787b299167069f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910615"
---
# <a name="example-handling-exceptions-when-binding-data"></a><span data-ttu-id="cb9c8-102">範例：處理繫結資料時所發生的例外狀況</span><span class="sxs-lookup"><span data-stu-id="cb9c8-102">Example: Handling Exceptions When Binding Data</span></span>
> [!NOTE]
> <span data-ttu-id="cb9c8-103">本主題討論 .NET 原生開發人員預覽，這是發行前版本的軟體。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="cb9c8-104">您可以從 [Microsoft Connect 網站](https://go.microsoft.com/fwlink/?LinkId=394611)下載預覽 (需要註冊)。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="cb9c8-105">下列範例顯示如何解決當以 .NET Native 工具鏈編譯的應用程式嘗試系結資料時, 所擲回的[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-105">The following example shows how to resolve a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) exception that is thrown when an app compiled with the .NET Native tool chain tries to bind data.</span></span> <span data-ttu-id="cb9c8-106">以下是例外狀況資訊：</span><span class="sxs-lookup"><span data-stu-id="cb9c8-106">Here’s the exception information:</span></span>  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:   
App.ViewModels.MainPageVM  
```  
  
 <span data-ttu-id="cb9c8-107">以下是相關聯的呼叫堆疊：</span><span class="sxs-lookup"><span data-stu-id="cb9c8-107">Here's the associated call stack:</span></span>  
  
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
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="cb9c8-108">應用程式做了什麼？</span><span class="sxs-lookup"><span data-stu-id="cb9c8-108">What was the app doing?</span></span>  
 <span data-ttu-id="cb9c8-109">在堆疊的基底, 來自<xref:Windows.UI.Xaml?displayProperty=nameWithType>命名空間的框架表示 XAML 轉譯引擎正在執行。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-109">At the base of the stack, frames from the <xref:Windows.UI.Xaml?displayProperty=nameWithType> namespace indicate that the XAML rendering engine was running.</span></span>   <span data-ttu-id="cb9c8-110">使用 <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> 方法會指出，在已移除中繼資料的類型上，以反映方式查閱屬性的值。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-110">The use of the <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> method indicates a reflection-based lookup of a property’s value on the type whose metadata was removed.</span></span>  
  
 <span data-ttu-id="cb9c8-111">提供中繼資料指示詞的第一個步驟，就是為該類型加入 `serialize` 中繼資料，讓它的所有屬性皆可供存取：</span><span class="sxs-lookup"><span data-stu-id="cb9c8-111">The first step in providing a metadata directive would be to add `serialize` metadata for the type so that its properties are all accessible:</span></span>  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="cb9c8-112">這是個案嗎？</span><span class="sxs-lookup"><span data-stu-id="cb9c8-112">Is this an isolated case?</span></span>  
 <span data-ttu-id="cb9c8-113">在這個案例中，如果資料繫結中有一個 `ViewModel` 的中繼資料不完整，其他的可能也一樣。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-113">In this scenario, if data binding has incomplete metadata for one `ViewModel`, it may for others, too.</span></span>  <span data-ttu-id="cb9c8-114">如果程式碼的結構化方式是應用程式的檢視模型全都在 `App.ViewModels` 命名空間中，您可以使用較為普遍的執行階段指示詞：</span><span class="sxs-lookup"><span data-stu-id="cb9c8-114">If the code is structured in a way that the app’s view models are all in the `App.ViewModels` namespace, you could use a more general runtime directive:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a><span data-ttu-id="cb9c8-115">可以將程式碼改寫為不使用反映嗎？</span><span class="sxs-lookup"><span data-stu-id="cb9c8-115">Could the code be rewritten to not use reflection?</span></span>  
 <span data-ttu-id="cb9c8-116">因為資料繫結是是反映密集作業，所以變更程式碼來避免反映並不可行。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-116">Because data binding is reflection-intensive, changing the code to avoid reflection isn’t feasible.</span></span>  
  
 <span data-ttu-id="cb9c8-117">不過，有一些方法可以將 `ViewModel` 指定至 XAML 頁面，讓工具鏈可以在編譯時將屬性繫結與正確的類型建立關聯，並且在不使用執行階段指示詞的情況下保留中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-117">However, there are ways to specify the `ViewModel` to the XAML page so that the tool chain can associate property bindings with the correct type at compile time and keep the metadata without using a runtime directive.</span></span>  <span data-ttu-id="cb9c8-118">例如, 您可以將<xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType>屬性套用在屬性上。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-118">For example, you could apply the <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribute on properties.</span></span> <span data-ttu-id="cb9c8-119">這會導致 XAML 編譯器產生必要的查閱資訊，並避免 Default.rd.xml 檔案中需要執行階段指示詞。</span><span class="sxs-lookup"><span data-stu-id="cb9c8-119">This causes the XAML compiler to generate the required lookup information and avoids requiring a runtime directive in the Default.rd.xml file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9c8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb9c8-120">See also</span></span>

- [<span data-ttu-id="cb9c8-121">快速入門</span><span class="sxs-lookup"><span data-stu-id="cb9c8-121">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="cb9c8-122">例如：針對動態程式設計進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="cb9c8-122">Example: Troubleshooting Dynamic Programming</span></span>](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)
