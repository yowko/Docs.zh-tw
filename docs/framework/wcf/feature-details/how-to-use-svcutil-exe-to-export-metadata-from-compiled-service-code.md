---
title: "HOW TO：使用 Svcutil.exe 來匯出已編譯服務程式碼的中繼資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e50ddaa5a9fe5038ef167c4a53f9600eda0f027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>HOW TO：使用 Svcutil.exe 來匯出已編譯服務程式碼的中繼資料
Svcutil.exe 可匯出服務中繼資料、合約以及編譯組件資料類型，如下：  
  
-   若要使用 Svcutil.exe 針對組件集合匯出所有編譯服務合約的中繼資料，請指定組件為輸入參數。 這是預設行為。  
  
-   若要使用 Svcutil.exe 針對編譯服務匯出中繼資料，請指定服務組件或將組件指定為輸入參數。 您必須使用 `/serviceName` 選項指示您想要匯出之服務的組態名稱。 Svcutil.exe 自動載入特定可執行組件的組態檔。  
  
-   若要匯出組件集合內所有資料合約類型，請使用 `/dataContractOnly` 選項。  
  
> [!NOTE]
>  使用 `/reference` 選項為任何相依組件指定檔案路徑。  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>若要匯出編譯服務合約的中繼資料  
  
1.  將您的服務合約實作編譯成一個或多個類別程式庫。1  
  
2.  執行 Svcutil.exe 處理編譯組件。  
  
    > [!NOTE]
    >  您可能需要使用 `/reference` 參數來指定任何相依組件的檔案路徑。  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>若要匯出編譯服務的中繼資料  
  
1.  將您的服務實作編譯為可執行組件  
  
2.  為您的服務可執行程式建立組態檔案並新增服務組態。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  使用 `/serviceName` 參數指定服務組態名稱，以 Svcutil.exe 處理編譯服務可執行檔。  
  
    > [!NOTE]
    >  您可能需要使用 `/reference` 參數來指定任何相依組件的檔案路徑。  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>若要匯出編譯資料合約的中繼資料  
  
1.  將您的資料合約實作編譯成一個或多個類別程式庫。  
  
2.  執行 Svcutil.exe 處理編譯組件，將 `/dataContract` 參數指定只產生資料合約的中繼資料。  
  
    > [!NOTE]
    >  您可能需要使用 `/reference` 參數來指定任何相依組件的檔案路徑。  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>範例  
 下列範例示範如何產生簡單服務實作與組態的中繼資料。  
  
 若要匯出服務合約的中繼資料  
  
```  
svcutil.exe Contracts.dll  
```  
  
 若要匯出資料合約的中繼資料  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 若要匯出服務實作的中繼資料  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` 為 Contracts.dll 的路徑。  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
