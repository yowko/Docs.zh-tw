---
title: "解析組件載入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0fe3347c640b7e99487d630cbfac97e774bda7bb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 解析組件載入
.NET Framework 為需要更充分掌控組件載入的應用程式提供了 <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> 事件。  藉由處理這個事件，您的應用程式就能從一般探查路徑將組件載入至載入內容、選取要載入的數個組件版本、發出動態組件及將它傳回等。  本主題提供處理 <xref:System.AppDomain.AssemblyResolve> 事件的指引。  
  
> [!NOTE]
>  若要解析僅限反映之內容中的組件負載，請改用 <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=fullName> 事件。  
  
## AssemblyResolve 事件的運作方式  
 當您為 <xref:System.AppDomain.AssemblyResolve> 事件註冊處理常式時，處理常式會在執行階段無法藉由名稱繫結至組件時叫用。  例如，從使用者程式碼呼叫下列方法可能導致引發 <xref:System.AppDomain.AssemblyResolve> 事件：  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName> 方法多載或 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法多載，它的第一個引數是字串，代表要載入之組件的顯示名稱 \(也就是 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName> 屬性要傳回的字串\)。  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName> 方法多載或 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法多載，它的第一個引數是識別要載入之組件的 <xref:System.Reflection.AssemblyName> 物件。  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> 方法多載。  
  
-   <xref:System.AppDomain.CreateInstance%2A?displayProperty=fullName> 或 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName> 方法多載，它會執行個體化另一個應用程式定義域中的物件。  
  
### 事件處理常式執行的工作  
 <xref:System.AppDomain.AssemblyResolve> 事件的處理常式會接收 <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> 屬性中，要載入之組件的顯示名稱。  如果處理常式無法辨識組件名稱，則會傳回 null \(在 Visual Basic 中為 `Nothing`，在 Visual C\+\+ 中則為 `nullptr`\)。  
  
 如果處理常式可辨識組件名稱，則可以載入和傳回符合要求的組件。  下列清單描述一些範例情節。  
  
-   如果處理常式知道某個版本組件的位置，則可以使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> 方法載入組件，如果成功的話，也可以傳回載入的組件。  
  
-   如果處理常式可以存取儲存為位元組陣列的組件資料庫，則可以使用其中一個採用位元組陣列的 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法多載。  
  
-   處理常式可以產生動態組件並將它傳回。  
  
> [!NOTE]
>  處理常式壁需將組件載入至載入來源內容、載入內容或無內容。  如果處理常式使用 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=fullName> 方法將組件載入至僅限反映內容，則引發 <xref:System.AppDomain.AssemblyResolve> 事件的載入嘗試會失敗。  
  
 處理常式必須負責傳回適合的組件。  處理常式可以藉由將 <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> 屬性值傳遞至 <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> 建構函式的方式，剖析所要求組件的顯示名稱。  從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]開始，處理常式可以使用 <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> 屬性判斷目前的要求是否相依於另一個組件。  這項資訊有助於識別將滿足相依性的組件。  
  
 事件處理常式可傳回與所要求版本不同的組件版本。  
  
 在大部分情況下，處理常式傳回的組件會出現在載入內容中，無論處理常式將它載入何種內容。  例如，如果處理常式使用 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> 方法將組件載入至載入來源內容，當處理常式傳回組件時，該組件會出現在載入內容中。  不過，在下列情況下，當處理常式傳回組件時，該組件會顯示為無內容狀態：  
  
-   處理常式載入無內容的組件。  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> 屬性不是 null。  
  
-   發出要求的組件 \(也就是 <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> 屬性傳回的組件\) 是在無內容的情況下載入。  
  
 如需有關內容的詳細資訊，請參閱 <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=fullName> 方法多載。  
  
 同一個應用程式定義域中可以載入同一個組件的多個版本。  不建議您採用這個做法，因為這樣可能導致型別指派的問題。  請參閱 [組件載入的最佳作法](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)。  
  
### 事件處理常式不應執行的工作  
 處理 <xref:System.AppDomain.AssemblyResolve> 事件的首要規則就是，您不應該嘗試傳回無法辨識的組件。  當您撰寫處理常式時，應該知道哪些組件可能引發事件。  您的處理常式應針對其他組件傳回 null。  
  
> [!IMPORTANT]
>  從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，會針對附屬組件引發 <xref:System.AppDomain.AssemblyResolve> 事件。  這項變更會影響針對舊版 .NET Framework 撰寫的事件處理常式 \(如果處理常式嘗試解析所有組件載入要求\)。  忽略無法辨識之組件的事件處理常式則不受這項變更的影響：它們會傳回 null，並且遵循一般後援機制。  
  
 載入組件時，事件處理常式不可使用可能反覆引發 <xref:System.AppDomain.AssemblyResolve> 事件的任何 <xref:System.AppDomain.Load%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法多載，因為這樣可能導致堆疊溢位 \(請參考本主題前段提供的清單\)。即使您針對載入要求提供例外狀況處理，這種情況仍然會發生，因為直到所有事件處理常式都傳回之後，才會擲回例外狀況。  因此，下列程式碼會在找不到 `MyAssembly` 時導致堆疊溢位：  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [組件載入的最佳做法](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)

