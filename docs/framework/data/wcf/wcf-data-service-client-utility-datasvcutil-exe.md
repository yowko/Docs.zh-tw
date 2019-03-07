---
title: WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: bb279e6fa16b82bffbebc777f791ce7a6e06255d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492643"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)

DataSvcUtil.exe 是命令列工具所使用的 WCF Data Services 提供[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要，並產生從.NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。 此公用程式可以透過使用下列中繼資料來源產生資料類別：

-   資料服務的根 URI。 此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。 如需詳細資訊，請參閱[OData:服務中繼資料文件](https://go.microsoft.com/fwlink/?LinkId=186070)。

-   定義使用概念結構定義語言 (CSDL) 中所定義的資料模型檔案 (.csdl) [ \[MC-CSDL\]:概念結構定義檔案格式](https://go.microsoft.com/fwlink/?LinkID=159072)規格。

-   使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。 如需詳細資訊，請參閱 < [ \[MC-EDMX\]:資料服務封裝格式的實體資料模型](https://go.microsoft.com/fwlink/?LinkID=178833)規格。

如需詳細資訊，請參閱[如何：手動產生用戶端資料服務類別](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。

DataSvcUtil.exe 工具安裝在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 目錄中。 在許多情況下，這位於*C:\Windows\Microsoft.NET\Framework\v4.0*。 適用於 64 位元系統，這位於*C:\Windows\Microsoft.NET\Framework64\v4.0*。 您也可以存取 DataSvcUtil.exe 工具從開發人員命令提示字元適用於 Visual Studio。

## <a name="syntax"></a>語法

```
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]
```

## <a name="parameters"></a>參數

|選項|描述|
|------------|-----------------|
|`/dataservicecollection`|指定同時產生將物件繫結至控制項所需的程式碼。|
|`/help`<br /><br /> -或-<br /><br /> `/?`|顯示工具的命令語法和選項。|
|`/in:` *\<file>*|指定 .csdl 或 .edmx 檔案，或是檔案所在的目錄。|
|`/language:`[VB&#124;CSharp]|指定所產生之原始程式碼檔案的語言。 預設語言為 C#。|
|`/nologo`|隱藏著作權訊息。|
|`/out:` *\<file>*|指定原始程式碼檔案的名稱，該檔案包含已產生的用戶端資料服務類別。|
|`/uri:` *\<string>*|OData 摘要的 URI。|
|`/version:`[1.0&#124;2.0]|指定 OData 的最高接受的版本。 版本取決於`DataServiceVersion`DataService 中項目的屬性傳回的資料服務中繼資料。 如需詳細資訊，請參閱 <<c0> [ 資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。 當您指定`/dataservicecollection`參數，您也必須指定`/version:2.0`以啟用資料繫結。|

## <a name="see-also"></a>另請參閱

- [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)
- [如何：加入資料服務參考](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
