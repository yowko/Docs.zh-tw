---
title: 自訂篩選器
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ade387524c9ca6c8ef337ccf6a5b3453b7df976b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945371"
---
# <a name="custom-filters"></a>自訂篩選器
自訂篩選可讓您定義無法使用系統所提供訊息篩選完成的比對邏輯。 例如，您可能會建立自訂篩選，此篩選會雜湊特殊訊息項目，然後檢查值，判斷篩選應傳回 true 或 false。  
  
## <a name="implementation"></a>實作  
 自訂篩選是 <xref:System.ServiceModel.Dispatcher.MessageFilter> 抽象基底類別的實作。 實作您的自訂篩選時，建構函式可以選擇性地接受單一字串參數。 此參數會包含傳遞至 MessageFilter 建構函式的組態資訊，以便提供篩選在執行階段執行比對時所需的任何值或組態。 例如，此參數可能用來提供篩選在要評估的訊息內尋找的值。 下列範例示範接受字串參數之自訂訊息篩選的基本實作：  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> 在實際的執行中, Match 方法包含的邏輯會檢查訊息, 以判斷此訊息篩選準則是否應傳回**true**或**false**。  
  
### <a name="performance"></a>效能  
 實作自訂篩選時，最好將篩選完成訊息評估所需的時間長度上限納入考量。 在找到相符項目之前，可能會根據多個篩選評估訊息，因此，確保用戶端要求在可以評估所有篩選之前沒有逾時相當重要。 為此，自訂篩選應該只包含評估訊息內容或屬性所需的程式碼，才能判斷該訊息是否符合篩選準則。  
  
 一般而言，實作自訂篩選時，您應該避免下列狀況：  
  
- IO，例如，將資料儲存到磁碟或資料庫。  
  
- 不必要的處理，例如，針對某個文件中的多筆記錄執行迴圈。  
  
- 封鎖作業，例如，與取得共用資源之鎖定或針對資料庫執行查詢有關的呼叫。  
  
 在實際執行環境中使用自訂篩選之前，您應該執行效能測試，以判斷篩選評估訊息所需的平均時間長度。 結合其他篩選在篩選資料表中使用之平均處理時間時，這可讓您正確判斷用戶端應用程式應該指定的最大逾時值。  
  
## <a name="usage"></a>使用量  
 若要搭配路由服務使用您的自訂篩選, 您必須指定類型為「自訂」、訊息篩選器的完整類型名稱和元件名稱的新篩選項目, 將其加入至篩選資料表。  就像使用其他 MessageFilters 一般，您可以指定 filterData 字串，這個字串將傳遞至自訂篩選的建構函式。  
  
 下列範例示範使用自訂篩選搭配路由服務：  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"   
            customType="CustomAssembly.MyMessageFilter,   
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
