---
title: 執行緒區域儲存區：執行緒相關的靜態欄位和資料位置
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a17bc509c8c82bfb30811ec3511207ca2d823e5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589850"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>執行緒區域儲存區：執行緒相關的靜態欄位和資料位置
您可以使用受控執行緒區域儲存區 (TLS) 來儲存對執行緒和應用程式定義域而言是唯一的資料。 .NET Framework 提供兩種方式來使用受控 TLS：執行緒相關的靜態欄位和資料插槽。  
  
-   如果您可以預期編譯時期的確切需求，請使用執行緒相關的靜態欄位 (在 Visual Basic 中為執行緒相關 `Shared` 欄位)。 執行緒相關靜態欄位提供最佳效能。 它們也提供編譯時期類型檢查的優點。  
  
-   若您的實際需求只能在執行階段進行探索，請使用資料插槽。 比起執行緒相關靜態欄位，資料插槽的速度更慢且更難使用，而且會將資料儲存為 <xref:System.Object> 型別，因此您必須將它轉換成正確的型別才能使用它。  
  
 在非受控 C++ 中，您可以使用 `TlsAlloc` 動態配置插槽，並使用 `__declspec(thread)` 來宣告變數應配置於執行緒相關儲存區中。 執行緒相關靜態欄位和資料插槽提供此行為的受控版本。  
  
 在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中，您可以使用 <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> 類別來建立第一次取用物件時進行延遲初始化的執行緒區域物件。 如需詳細資訊，請參閱[延遲初始化](../../../docs/framework/performance/lazy-initialization.md)。  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>受控 TLS 中資料的唯一性  
 無論您使用的是執行緒相關靜態欄位或資料插槽，受控 TLS 中的資料對執行緒和應用程式定義域的組合都是唯一的。  
  
-   在應用程式定義域內，一個執行緒無法修改另一個執行緒的資料，即使這兩個執行緒使用同一個欄位或插槽也一樣。  
  
-   當執行緒從多個應用程式定義域存取相同的欄位或插槽時，會在每個應用程式定義域中維護個別的值。  
  
 例如，如果執行緒會設定執行緒相關靜態欄位的值，則進入另一個應用程式定義域，然後擷取該欄位的值，在第二個應用程式定義域中擷取的值與第一個應用程式定義域中的值不同。 在第二個應用程式定義域中設定欄位的新值，不會影響欄位在第一個應用程式定義域中的值。  
  
 同樣地，當執行緒取得兩個不同應用程式定義域中相同的具名資料插槽時，第一個應用程式定義域中的資料會維持獨立，與第二個應用程式定義域中的資料無關。  
  
## <a name="thread-relative-static-fields"></a>執行緒相關靜態欄位  
 如果您知道某份資料對執行緒和應用程式定義域組合而言一定是唯一的，請將 <xref:System.ThreadStaticAttribute> 屬性套用到靜態欄位。 像使用任何其他靜態欄位一樣使用此欄位。 欄位中的資料對使用它的每個執行緒而言都是唯一的。  
  
 執行緒相關靜態欄位提供比資料插槽更好的效能，並具備編譯時期型別檢查的優點。  
  
 請注意，任何類別建構函式程式碼都將在存取欄位之第一個內容的第一個執行緒上執行。 在相同應用程式定義域的所有其他執行緒或內容中，如果它們為參考型別，就會將欄位初始化為 `null` (在 Visual Basic 中為 `Nothing`)，或者如果它們是實值型別，則會設為預設值。 因此，您不應該依賴類別建構函式來將執行緒相關靜態欄位初始化。 而是應避免將執行緒相關靜態欄位初始化，並假設已將它們初始化為 `null` (`Nothing`) 或其預設值。  
  
## <a name="data-slots"></a>資料插槽  
 .NET Framework 提供動態資料插槽，這些插槽對執行緒和應用程式定義域的組合而言都是唯一的。 有兩種類型的資料插槽：具名插槽和未命名的插槽。 這兩者都使用 <xref:System.LocalDataStoreSlot> 結構來實作。  
  
-   若要建立具名資料插槽，使用 <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> 方法。 若要取得現有具名插槽的參考，將其名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法。  
  
-   若要建立未命名的資料插槽，請使用 <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> 方法。  
  
 針對具名和未命名的插槽，請使用 <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> 方法來設定和擷取插槽中的資訊。 這些靜態方法一律會根據目前正在執行它們之執行緒的資料來動作。  
  
 具名插槽很方便，因為當您需要擷取該插槽時，您可以透過將其名稱傳遞至 <xref:System.Threading.Thread.GetNamedDataSlot%2A> 方法來完成，而不需維護未命名插槽的參考。 不過，如果另一個元件針對其執行緒相關儲存區使用相同名稱，而且執行緒會執行來自您的元件和另一個元件的程式碼，則這兩個元件可能會損毀彼此的資料 (此案例假設這兩個元件正在相同的應用程式定義域中執行，而且它們並未設計來共用相同資料)。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [執行緒處理](../../../docs/standard/threading/index.md)
