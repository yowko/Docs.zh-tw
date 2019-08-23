---
title: 訊息篩選條件
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: b8de58b6935ee59fc8c787dfcf7445afcd0774b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912692"
---
# <a name="message-filters"></a>訊息篩選條件
為了實作內容架構路由，路由服務會使用 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作，該實作會檢查訊息的特定區段，例如位址、端點名稱或特定 XPath 陳述式。 如果 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 提供的訊息篩選都不符合您的需要，您可以建立透過建立新的基底 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別實作來建立自訂篩選。  
  
 設定路由服務時, 您必須定義篩選元素 (<xref:System.ServiceModel.Routing.Configuration.FilterElement>物件) 來描述**MessageFilter**的類型, 以及建立篩選所需的任何支援資料, 例如要在訊息內搜尋的特定字串值. 請注意，建立篩選項目只會定義個別訊息篩選，若要使用篩選評估和路由傳送訊息，您還必須定義篩選資料表 (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>)。  
  
 篩選資料表中的每個項目都會參考篩選項目，並且指定將路由傳送訊息的目標用戶端端點 (如果訊息符合篩選的話)。 篩選資料表項目還可讓您指定備份端點的集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)，該集合會定義端點清單，當傳送至主要端點期間發生傳輸失敗事件時，會將訊息傳送至這些端點。 這些端點會依指定的順序嘗試，直到其中一個成功為止。  
  
## <a name="message-filters"></a>訊息篩選條件  
 路由服務使用的訊息篩選提供一般訊息選取功能，例如評估做為訊息傳送目標的端點名稱、SOAP 動作，或做為訊息傳送目標的位址或位址前置詞。 篩選也可以聯結 `AND` 條件，如此一來，只有在訊息同時符合兩個篩選時，才會路由傳送至端點。 您也可以透過建立自己的 <xref:System.ServiceModel.Dispatcher.MessageFilter> 實作來建立自訂篩選。  
  
 下表列出路由服務使用的 <xref:System.ServiceModel.Routing.Configuration.FilterType>、實作特定訊息篩選的類別，以及必要的 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> 參數。  
  
|篩選條件類型|描述|篩選資料意義|範例篩選|  
|------------------|-----------------|-------------------------|--------------------|  
|動作|使用 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> 類別比對包含特定動作的訊息。|要進行篩選的動作。|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|EndpointAddress|<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>使用類別<xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> 搭配來比對包含特定位址的訊息。 ==  `true`|要篩選的位址 (在 [收件者] 標頭中)。|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|EndpointAddressPrefix|<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>使用類別<xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> 搭配來比對包含特定位址前置詞的訊息。 ==  `true`|要使用最長的前置詞比對篩選的位址。|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|和|使用固定在傳回之前評估兩項條件的 <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> 類別。|未使用 filterData;相反地, filter1 和 filter2 會有對應的訊息篩選器名稱 (也在資料表中), 這應該是**和**ed。|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|自訂|使用者定義類型，該類型會延伸 <xref:System.ServiceModel.Dispatcher.MessageFilter> 類別並且擁有取用字串的建構函式。|customType 屬性是要建立之類別的完整類型名稱；filterData 則是建立篩選時，要傳遞至建構函式的字串。|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|EndpointName|使用 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> 類別，根據訊息到達的服務端點名稱比對訊息。|服務端點的名稱, 例如: "serviceEndpoint1"。  這應該是在路由服務上公開的其中一個端點。|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|MatchAll|使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> 類別。 此篩選會比對所有抵達的訊息。|不會使用 filterData。 此篩選將固定比對所有訊息。|\<filter name="matchAll1" filterType="MatchAll" />|  
|XPath|使用 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 類別比對訊息內的特定 XPath 查詢。|比對訊息時使用的 XPath 查詢。|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 下列範例會定義使用 XPath、EndpointName 和 PrefixEndpointAddress 訊息篩選的篩選項目。 此範例也會示範針對 RoundRobinFilter1 和 RoundRobinFilter2 項目使用自訂篩選。  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"   
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"   
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"   
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"   
             customType="RoutingServiceFilters.RoundRobinMessageFilter,   
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> 只定義篩選並不會針對該篩選評估訊息。 篩選必須加入至篩選資料表，接著篩選資料表會與路由服務公開的服務端點產生關聯。  
  
### <a name="namespace-table"></a>命名空間資料表  
 使用 XPath 篩選時，包含 XPath 查詢的篩選資料可能因為使用命名空間而變得相當大。 為了減輕此問題所造成的影響，路由服務提供了一項功能，讓您使用命名空間資料表定義自己的命名空間前置詞。  
  
 命名空間資料表是 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> 物件的集合，該集合會定義可在 XPath 中使用之通用命名空間的命名空間前置詞。 以下為命名空間資料表中包含的預設命名空間和命名空間前置詞。  
  
|前置詞|命名空間|  
|------------|---------------|  
|s11|`http://schemas.xmlsoap.org/soap/envelope`|  
|s12|`http://www.w3.org/2003/05/soap-envelope`|  
|wsaAugust2004|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|wsa10|`http://www.w3.org/2005/08/addressing`|  
|/sm|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|tempuri|`http://tempuri.org`|  
|ser|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 如果您事先知道將會在 XPath 查詢中使用特定命名空間，可以將它與唯一的命名空間前置詞一起加入至命名空間資料表，並且在任何 XPath 查詢中使用該前置詞，而不要使用完整的命名空間。 下列範例會針對命名空間`"http://my.custom.namespace"`定義 "custom" 的前置詞, 然後用於 filterData 中包含的 XPath 查詢。  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a>篩選資料表  
 雖然每一個篩選項目都會定義可套用至訊息的邏輯比較，但是篩選資料表仍然會提供篩選項目和目的用戶端端點之間的關聯。 篩選資料表是具名的 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> 物件集合，會定義篩選、主要目的端點和替代備份端點清單之間的關聯。 篩選資料表項目還可讓您針對每一項篩選條件指定選擇性的優先順序。 下列範例會定義兩個篩選，然後定義篩選資料表，讓每個篩選與目的端點產生關聯。  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>      
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a>篩選評估優先權  
 根據預設，篩選資料表中的所有項目會同步評估，所評估的訊息會路由傳送至與每個相符篩選項目相關聯的端點。 如果有多個篩選評估為 `true`，而訊息為單向或雙工，則訊息會多點傳送至所有相符篩選的端點。 但是要求-回覆訊息無法多點傳送，因為只能將一個回覆傳回至用戶端。  
  
 透過指定每個篩選的優先權層級，就可以實作更為複雜的路由邏輯，路由服務會先評估優先權層級最高的所有篩選。 如果訊息符合此層級的篩選，則不會處理較低優先權的篩選。 例如，傳入的單向訊息會先針對優先權為 2 的所有篩選進行評估。 訊息不符合此優先權層級的任何篩選，因此接著會針對優先權 1 的篩選比較訊息。 有兩個優先權 1 的篩選符合訊息，而因為這是單向訊息，因此會路由傳送至這兩個目的端點。  由於在優先權 1 的篩選中找到相符項目，因此不會評估優先權 0 的篩選。  
  
> [!NOTE]
> 如果未指定任何篩選，則會使用預設優先權 0。  
  
 下列範例會定義篩選資料表，針對資料表中參考的篩選指定優先權 2、1 和 0。  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"   
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"   
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"   
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"   
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 在前面的範例中，如果訊息符合 XPathFilter，則會路由傳送至 roundingCalcEndpoint，並且不會再評估資料表中的任何篩選，因為所有其他篩選都屬於較低的優先權。 不過，如果訊息不符合 XPathFilter，會接著針對下一個較低優先權的所有篩選 EndpointNameFilter 和 PrefixAddressFilter 進行評估。  
  
> [!NOTE]
> 如果可行，請使用互斥的篩選，而不要指定優先權，因為優先權評估可能導致效能降低。  
  
### <a name="backup-lists"></a>備份清單  
 篩選資料表中的每一個篩選可以選擇性地指定備份清單，也就是具名的端點集合 (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>)。 此集合包含依順序排列的端點清單，訊息將在傳送至 <xref:System.ServiceModel.CommunicationException> 中指定的主要端點期間發生 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> 時，傳輸至這些端點。 下列範例會定義名為 "backupServiceEndpoints" 的備份清單, 其中包含兩個端點。  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 在上述範例中, 如果傳送至主要端點「目的地」失敗, 則路由服務會嘗試以列出的順序將每個端點傳送到每個端點, 先傳送至 backupServiceQueue, 然後在傳送至 backupServiceQueue 失敗。 如果所有備份端點都失敗，則會傳回錯誤。
