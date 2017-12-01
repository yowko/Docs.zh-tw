---
title: "執行緒區域儲存區：執行緒相關的靜態欄位和資料位置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>執行緒區域儲存區：執行緒相關的靜態欄位和資料位置
您可以使用 managed 的執行緒區域儲存區 (TLS) 來儲存資料的唯一執行緒和應用程式網域。 .NET Framework 提供兩種方式使用受管理的 TLS： 執行緒相關靜態欄位和資料位置。  
  
-   使用執行緒相關的靜態欄位 (執行緒相關`Shared`在 Visual Basic 中的欄位) 如果您可以預期會在編譯時期的確切需求。 執行緒相關的靜態欄位會提供最佳效能。 它們也提供編譯階段類型檢查的好處。  
  
-   實際的需求可能會發現只能在執行階段時，請使用 資料位置。 資料位置較慢，多執行緒相關的靜態欄位，而造成不便，資料會儲存為類型<xref:System.Object>，因此您必須將它轉換成正確的型別再使用它。  
  
 在 unmanaged c + + 中，您可以使用`TlsAlloc`動態配置位置和`__declspec(thread)`來宣告變數，應配置執行緒相關的儲存體中。 相對執行緒的靜態欄位和資料位置提供的受管理的版本，此行為。  
  
 在[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>類別以建立第一次取用物件時執行延遲初始化執行緒區域物件。 如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>受管理的 TLS 中的資料的唯一性  
 無論您是使用執行緒相關的靜態欄位或資料的位置，受管理的 TLS 中的資料是唯一的執行緒和應用程式定義域的組合。  
  
-   應用程式定義域內兩個執行緒使用的同一個欄位或位置時，即使一個執行緒時，無法修改來自另一個執行緒，資料。  
  
-   當執行緒存取相同的欄位或位置，從多個應用程式定義域時，每個應用程式定義域中維護個別的值。  
  
 例如，如果執行緒設定執行緒相關的靜態欄位的值會在進入另一個應用程式定義域，並接著會擷取欄位的值，擷取第二個應用程式定義域中的值不同於第一個應用程式定義域中的值。 設定第二個應用程式定義域中的新值的欄位不會影響欄位的第一個應用程式定義域中的值。  
  
 同樣地，當執行緒會取得兩個不同的應用程式網域中相同的具名的資料位置，第一個應用程式網域中的資料會維持獨立於第二個應用程式網域中的資料。  
  
## <a name="thread-relative-static-fields"></a>執行緒相關的靜態欄位  
 如果您知道某份資料一定是唯一的執行緒和應用程式定義域的組合，套用<xref:System.ThreadStaticAttribute>屬性到靜態欄位。 如同您使用任何其他靜態欄位，請使用欄位。 欄位中的資料是使用它的每個執行緒的唯一的。  
  
 執行緒相關的靜態欄位提供較佳的效能比資料位置，並有編譯時間類型檢查的好處。  
  
 請注意，任何類別建構函式程式碼會存取欄位的第一個內容中的第一個執行緒上執行。 在所有其他執行緒或內容相同的應用程式定義域中，欄位將初始化為`null`(`Nothing`在 Visual Basic 中) 如果它們都是參考類型，或設為預設值，如果它們是實值類型。 因此，您不應該依賴類別建構函式來初始化執行緒相關的靜態欄位。 相反地，請避免初始化執行緒相關的靜態欄位，並假設已初始化為`null`(`Nothing`) 或為其預設值。  
  
## <a name="data-slots"></a>資料位置  
 .NET Framework 提供動態的資料位置對執行緒和應用程式定義域的組合都是唯一。 有兩種類型的資料位置： 具名位置和未命名的位置。 兩者都透過使用實作<xref:System.LocalDataStoreSlot>結構。  
  
-   若要建立具名的資料位置，請使用<xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType>或<xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>方法。 若要取得現有的具名位置的參考，傳遞至其名稱<xref:System.Threading.Thread.GetNamedDataSlot%2A>方法。  
  
-   若要建立未命名的資料位置，請使用<xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType>方法。  
  
 針對名為和未命名的位置，使用<xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType>和<xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>方法設定和擷取的位置中的資訊。 這些是永遠作用於目前執行它們的執行緒資料的靜態方法。  
  
 具名的位置很方便，因為當您需要藉由傳遞至其名稱時，您可以擷取插槽<xref:System.Threading.Thread.GetNamedDataSlot%2A>方法，而不是維護的參考未命名的位置。 不過，如果另一個元件使用相同的名稱，其執行緒相關的儲存體和執行緒執行程式碼從您的元件和其他元件，兩個元件可能會損毀彼此的資料。 （此案例假設這兩個元件，相同的應用程式定義域中執行，而他們並非設計來共用相同的資料）。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [執行緒處理](../../../docs/standard/threading/index.md)
