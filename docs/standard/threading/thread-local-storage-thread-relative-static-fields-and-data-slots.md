---
title: "Thread Local Storage: Thread-Relative Static Fields and Data Slots | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], local storage"
  - "threading [.NET Framework], thread-relative static fields"
  - "local thread storage"
  - "TLS"
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Thread Local Storage: Thread-Relative Static Fields and Data Slots
您可使用 Managed 執行緒區域儲存區 \(Thread Local Storage，TLS\) 來儲存對執行緒及應用程式定義域來說是唯一的資料。  .NET Framework 提供兩種方法來使用 Managed TLS：執行緒相關的靜態欄位和資料位置。  
  
-   如果您可預期於編譯時期的確切需求，可以使用執行緒相關的靜態欄位 \(在 Visual Basic 中為執行緒相關 `Shared` 欄位\)。  執行緒相關的靜態欄位可提供最佳效能。  這也提供您在編譯時期檢查型別的好處。  
  
-   如果只能於執行階段得知實際的需求，則請使用資料位置。  與執行緒相關的靜態欄位相較，資料位置較慢，使用起來也較為複雜，而且資料會儲存成型別 <xref:System.Object>，因此在使用之前必須先轉換成正確的型別。  
  
 在 Unmanaged C\+\+ 中，您會使用 `TlsAlloc` 動態配置位置以及使用 `__declspec(thread)` 宣告變更應配置在執行緒相關儲存區中。  執行緒相關的靜態欄位和資料位置則提供這個行為的 Managed 版本。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，您可以使用 <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 類別，在物件首次使用時建立延遲初始化的執行緒區域物件。  如需詳細資訊，請參閱[延遲初始設定](../../../docs/framework/performance/lazy-initialization.md)。  
  
## Managed TLS 中的資料唯一性  
 無論使用的是執行緒相關的靜態欄位或是資料位置，Managed TLS 中的資料對執行緒及應用程式定義域的組合來說都是唯一的。  
  
-   在應用程式定義域內，即使兩個執行緒使用同一欄位或位置，其中一個執行緒也不能從另一個執行緒修改資料。  
  
-   當執行緒從多個應用程式定義域存取同一欄位或位置時，每個應用程式定義域中會各保有一個值。  
  
 例如，如果執行緒設定執行緒相關靜態欄位的值、進入另一個應用程式定義域，然後擷取該欄位的值，則在第二個應用程式定義域擷取的值會與第一個應用程式定義域中的值不同。  在第二個應用程式定義域中為欄位設定新值，不會影響該欄位在第一個應用程式定義域中的值。  
  
 同樣地，當執行緒在兩個不同的應用程式定義域中取得名稱相同的資料位置時，第一個應用程式定義域中的資料會維持獨立，與第二個應用程式定義域中的資料不相關。  
  
## 執行緒相關的靜態欄位  
 如果您知道某項資料對執行緒和應用程式定義域的組合而言永遠是唯一的，請將 <xref:System.ThreadStaticAttribute> 屬性套用到靜態欄位。  使用此欄位的方式與其他靜態欄位的使用方式相同。  欄位中的資料對每個使用它的執行緒來說都是唯一的。  
  
 執行緒相關的靜態欄位所提供的效能比資料位置更好，而且還有編譯時期型別檢查的好處。  
  
 請注意，任何類別建構函式 \(Constructor\) 程式碼均會在存取欄位的第一個內容中的第一個執行緒上執行。  在相同應用程式定義域內的所有其他執行緒或內容中，如果欄位是參考型別，這些欄位將會初始化為 `null` \(在 Visual Basic 中為 `Nothing`\)，如果欄位是實值型別，就會初始化為其預設值。  因此，您不應依賴類別建構函式來初始化執行緒相關的靜態欄位，  而應避免初始化執行緒相關的靜態欄位，並假設它們都是初始化為 `null` \(`Nothing`\) 或其預設值。  
  
## 資料位置  
 .NET Framework 提供對執行緒和應用程式定義域組合來說是唯一的動態資料位置。  有命名的位置及未命名的位置等兩種資料位置。  這兩者都是使用 <xref:System.LocalDataStoreSlot> 結構實作的。  
  
-   若要建立具名資料位置，請使用 <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=fullName> 或 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=fullName> 方法。  若要取得現有具名位置的參考，請將其名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法。  
  
-   若要建立不具名的資料位置，請使用 <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=fullName> 方法。  
  
 針對具名和不具名的位置，使用 <xref:System.Threading.Thread.SetData%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.GetData%2A?displayProperty=fullName> 方法可設定和擷取位置中的資訊。  這些是靜態方法，永遠會針對目前執行它們的執行緒操作資料。  
  
 具名位置很方便，因為只要在需要時將位置的名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法，便可以擷取位置，而無須維護不具名位置的參考。  不過，如果另一個元件也使用這個相同的名稱做為它的執行緒相關儲存區，而且執行緒可以從您的元件和其他元件執行程式碼，那麼這兩個元件可能會損毀彼此的資料\(此情況假設兩個元件都在同一個應用程式定義域中執行，而且並未設計成共用相同的資料\)。  
  
## 請參閱  
 <xref:System.ContextStaticAttribute>   
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=fullName>   
 <xref:System.ThreadStaticAttribute>   
 <xref:System.Runtime.Remoting.Messaging.CallContext>   
 [Threading](../../../docs/standard/threading/index.md)