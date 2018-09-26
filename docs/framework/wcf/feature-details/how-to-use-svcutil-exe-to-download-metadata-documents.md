---
title: HOW TO：使用 Svcutil.exe 來下載中繼資料文件
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 6643f0a5dba98afcef38870cf24d91e7d69a1440
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195416"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>HOW TO：使用 Svcutil.exe 來下載中繼資料文件
您可以使用 Svcutil.exe 從正在執行的服務下載中繼資料，並將該中繼資料儲存至本機檔案。 對於 HTTP 和 HTTPS URL 配置，Svcutil.exe 會嘗試使用 Ws-metadataexchange 擷取中繼資料並[XML Web Service 探索](https://go.microsoft.com/fwlink/?LinkId=94950)。 對於所有其他的 URL 配置，Svcutil.exe 只會使用 WS-MetadataExchange。  
  
 根據預設，Svcutil.exe 會使用定義於 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別的繫結。 若要設定用於 WS-MetadataExchange 的繫結，您必須在 Svcutil.exe 的組態檔 (svcutil.exe.config) 中定義用戶端端點，該端點會使用 `IMetadataExchange` 合約，而且使用名稱就是中繼資料端點位址的統一資源識別元 (URI) 配置。  
  
> [!CAUTION]
> 當執行 Svcutil.exe 以取得中繼資料服務公開兩個不同的服務合約，每個包含相同名稱的作業時，Svcutil.exe 會顯示錯誤說: 「 無法取得中繼資料從...」比方說，如果您有公開 （expose） 呼叫的服務合約的服務`ICarService`具有作業`Get(Car c)`相同的服務會公開稱為 「 服務合約`IBookService`具有作業`Get(Book b)`。 為了解決此問題，請執行下列其中一項：
>
> - 重新命名其中一項作業。
> - 將 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 設定為另一個名稱。
> - 使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性，將其中一項作業的命名空間設定為另一個命名空間。
  
## <a name="to-download-metadata-using-svcutilexe"></a>使用 Svcutil.exe 來下載中繼資料  
  
1.  在下列位置找到 Svcutil.exe 工具：  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  在命令提示字元中，使用下列格式啟動該工具。  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     您必須指定 `/t:metadata` 選項才能下載中繼資料。 否則，便會產生用戶端程式碼與組態。  
  
3.  <`url`> 引數指定的 url 提供服務端點的中繼資料或是線上裝載之中繼資料文件 URL。 <`epr`> 引數會指定要包含之 Ws-addressing 的 XML 檔案的路徑`EndpointAddress`支援 Ws-metadataexchange 之服務端點。  
  
 如需使用此工具來下載中繼資料的其他選項，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
## <a name="example"></a>範例  
 下列命令會從正在執行的服務下載中繼資料文件。  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>另請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
