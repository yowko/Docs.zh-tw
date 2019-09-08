---
title: 風險降低：在應用程式定義域之間將物件還原序列化
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d172503cee4e3880f493c68d5789e17c64a82a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790007"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>風險降低：在應用程式定義域之間將物件還原序列化
在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式定義域時，嘗試在跨應用程式定義域的邏輯呼叫內容中將物件還原序列化，將會擲回例外狀況。  
  
## <a name="diagnosing-the-issue"></a>診斷問題  
 下面這些情況會引發問題：  
  
1. 應用程式使用具有不同應用程式基底的兩個或多個應用程式定義域。  
  
2. 某些類型透過呼叫 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> 或 <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> 這類方法明確加入至 <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>。 這些類型並未標示為可序列化，而且未儲存在全域組件快取中。  
  
3. 在非預設應用程式定義域中執行的程式碼之後就會嘗試從組態檔讀取值，或使用 XML 將物件還原序列化。  
  
4. 為了要從組態檔讀取或將物件還原序列化，<xref:System.Xml.XmlReader> 物件會嘗試存取組態系統。  
  
5. 如果組態系統尚未初始化，則必須先完成初始化。 這表示，除此之外執行階段還必須為組態系統建立穩定的路徑，它會這樣做：  
  
    1. 它會尋找非預設應用程式定義域的辨識項。  
  
    2. 它會根據預設應用程式定義域，嘗試計算非預設應用程式定義域的辨識項。  
  
    3. 為了取得預設應用程式定義域的辨識項發出的呼叫，會觸發從非預設應用程式定義域到預設應用程式定義域的跨應用程式定義域呼叫。  
  
    4. 在 .NET Framework 的跨應用程式定義域合約中，邏輯呼叫內容中的內容同樣必須跨應用程式定義域的界限進行封送處理。  
  
6. 由於邏輯呼叫內容中的類型無法在預設應用程式定義域中解析，因此會擲回例外狀況。  
  
## <a name="mitigation"></a>緩和  
 若要解決這個問題，請執行下列動作  
  
1. 尋找擲回例外狀況時，在呼叫堆疊上的 `get_Evidence` 呼叫。 例外狀況可以是例外狀況的任一個大型子集，包括 <xref:System.IO.FileNotFoundException> 和 <xref:System.Runtime.Serialization.SerializationException>。  
  
2. 找出應用程式中沒有任何物件加入至邏輯呼叫內容的位置，並且加入下列程式碼：  
  
    ```  
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```  
  
## <a name="see-also"></a>另請參閱

- [執行階段變更](runtime-changes-in-the-net-framework-4-5-1.md)
