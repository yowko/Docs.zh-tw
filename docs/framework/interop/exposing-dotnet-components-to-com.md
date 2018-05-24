---
title: 將 .NET Framework 元件公開給 COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f11928388dba9b0e9b442578bfb7b6f751c2e172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="5abe5-102">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="5abe5-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="5abe5-103">撰寫 .NET 類型和從 Unmanaged 程式碼取用該類型，對開發人員來說是不同的活動。</span><span class="sxs-lookup"><span data-stu-id="5abe5-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="5abe5-104">本節描述幾個撰寫與 COM 用戶端交互操作之 Managed 程式碼的祕訣：</span><span class="sxs-lookup"><span data-stu-id="5abe5-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="5abe5-105">[限定交互操作的 .NET 類型](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)。</span><span class="sxs-lookup"><span data-stu-id="5abe5-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="5abe5-106">所有您想要公開給 COM 的 Managed 類型、方法、屬性、欄位和事件，都必須是公用的。</span><span class="sxs-lookup"><span data-stu-id="5abe5-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="5abe5-107">類型必須有公用的預設建構函式，它是唯一可透過 COM 叫用的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5abe5-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="5abe5-108">[套用 Interop 屬性](../../../docs/framework/interop/applying-interop-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="5abe5-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="5abe5-109">Managed 程式碼中的自訂屬性，可以加強元件的互通性。</span><span class="sxs-lookup"><span data-stu-id="5abe5-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="5abe5-110">[封裝 COM 的組件](../../../docs/framework/interop/packaging-an-assembly-for-com.md)。</span><span class="sxs-lookup"><span data-stu-id="5abe5-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="5abe5-111">COM 開發人員可能會要求您彙總參考及部署組件的相關步驟。</span><span class="sxs-lookup"><span data-stu-id="5abe5-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="5abe5-112">此外，本節還會找出與從 COM 用戶端取用 Managed 類型的相關工作。</span><span class="sxs-lookup"><span data-stu-id="5abe5-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="5abe5-113">從 COM 取用 Managed 類型</span><span class="sxs-lookup"><span data-stu-id="5abe5-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="5abe5-114">[向 COM 登錄組件](../../../docs/framework/interop/registering-assemblies-with-com.md)。</span><span class="sxs-lookup"><span data-stu-id="5abe5-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="5abe5-115">組件 (與型別程式庫) 中的類型必須在設計階段登錄。</span><span class="sxs-lookup"><span data-stu-id="5abe5-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="5abe5-116">如果安裝程式不登錄組件，請指示 COM 開發人員使用 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="5abe5-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="5abe5-117">[參考 COM 的 .NET 類型](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)。</span><span class="sxs-lookup"><span data-stu-id="5abe5-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="5abe5-118">COM 開發人員可以使用目前所用的相同工具和技術，參考組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="5abe5-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="5abe5-119">[呼叫 .NET 物件](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="5abe5-119">[Call a .NET object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).</span></span>  
  
     <span data-ttu-id="5abe5-120">COM 開發人員可以用在任何 Unmanaged 類型上呼叫方法的相同方式，在 .NET 物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="5abe5-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="5abe5-121">例如，COM **CoCreateInstance** API 會啟動 .NET 物件。</span><span class="sxs-lookup"><span data-stu-id="5abe5-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="5abe5-122">[部署供 COM 存取的應用程式](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="5abe5-122">[Deploy an application for COM access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).</span></span>  
  
     <span data-ttu-id="5abe5-123">強式名稱組件可以安裝在全域組件快取，而且需要其發行者的簽章。</span><span class="sxs-lookup"><span data-stu-id="5abe5-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="5abe5-124">沒有強式名稱的組件必須安裝在用戶端的應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="5abe5-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5abe5-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="5abe5-125">See Also</span></span>  
 [<span data-ttu-id="5abe5-126">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="5abe5-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="5abe5-127">COM Interop 範例：COM 用戶端與 .NET 伺服器</span><span class="sxs-lookup"><span data-stu-id="5abe5-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
