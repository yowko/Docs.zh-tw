---
title: 作法：使用 Svcutil.exe 來下載中繼資料文件
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 25840247e59b9dd61cadaa2ee94713240d135f88
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991606"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>作法：使用 Svcutil.exe 來下載中繼資料文件
您可以使用 Svcutil.exe 從正在執行的服務下載中繼資料，並將該中繼資料儲存至本機檔案。 針對 HTTP 和 HTTPS URL 配置，Svcutil 會嘗試使用透過 ws-metadataexchange 和[XML Web Service 探索](https://go.microsoft.com/fwlink/?LinkId=94950)來取得中繼資料。 對於所有其他的 URL 配置，Svcutil.exe 只會使用 WS-MetadataExchange。  
  
 根據預設，Svcutil.exe 會使用定義於 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別的繫結。 若要設定用於 WS-MetadataExchange 的繫結，您必須在 Svcutil.exe 的組態檔 (svcutil.exe.config) 中定義用戶端端點，該端點會使用 `IMetadataExchange` 合約，而且使用名稱就是中繼資料端點位址的統一資源識別元 (URI) 配置。  
  
> [!CAUTION]
> 當執行 Svcutil 來取得服務的中繼資料，而這兩個服務合約分別包含相同名稱的作業時，Svcutil 會顯示一則錯誤，指出「無法取得來自 ... 的中繼資料」。例如，如果您的`ICarService`服務會公開名為且具有`Get(Car c)`作業的服務合約，而且相同的服務會公開`Get(Book b)`名`IBookService`為且具有作業的服務合約。 為了解決此問題，請執行下列其中一項：
>
> - 重新命名其中一項作業。
> - 將 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 設定為另一個名稱。
> - 使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性，將其中一項作業的命名空間設定為另一個命名空間。
  
## <a name="to-download-metadata-using-svcutilexe"></a>使用 Svcutil.exe 來下載中繼資料  
  
1. 在下列位置找到 Svcutil.exe 工具：  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2. 在命令提示字元中，使用下列格式啟動該工具。  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     您必須指定 `/t:metadata` 選項才能下載中繼資料。 否則，便會產生用戶端程式碼與組態。  
  
3. <`url`> 引數會指定提供中繼資料之服務端點的 URL，或是線上裝載之元資料檔案的 URL。 <`epr`> 引數會指定 XML 檔案的路徑，該檔案包含支援透過 ws-metadataexchange 之`EndpointAddress`服務端點的 ws-addressing。  
  
 如需有關使用此工具來下載中繼資料的更多選項，請參閱[System.servicemodel 中繼資料公用程式工具（Svcutil .exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
## <a name="example"></a>範例  
 下列命令會從正在執行的服務下載中繼資料文件。  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>另請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
