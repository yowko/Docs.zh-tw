---
title: WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
ms.openlocfilehash: 600cb9a4f91ff2051f60ee86d4cb80cc5b404c61
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544293"
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a>WCF 資料服務用戶端公用程式 (DataSvcUtil.exe)

DataSvcUtil.exe 是 WCF Data Services 所提供的命令列工具，它會使用開放式資料通訊協定 (OData) 摘要，並產生從 .NET Framework 用戶端應用程式存取資料服務所需的用戶端資料服務類別。 此公用程式可以透過使用下列中繼資料來源產生資料類別：

- 資料服務的根 URI。 此公用程式會要求服務中繼資料文件，以描述資料服務所公開的資料模型。 如需詳細資訊，請參閱 [AtomPub (rfc5023 會) ](https://tools.ietf.org/html/rfc5023#section-8)。

- 使用概念結構定義語言 (CSDL) （如[ \[ MC-csdl \] ：概念結構定義檔案格式](/openspecs/windows_protocols/mc-csdl/c03ad8c3-e8b7-4306-af96-a9e52bb3df12)規格中所定義）所定義的資料模型檔 ( csdl) 。

- 使用 Entity Framework 提供之實體資料模型所建立的 .edmx 檔案。 如需詳細資訊，請參閱[ \[ MC-EDMX \] ：適用于資料服務封裝格式](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16)規格的實體資料模型。

如需詳細資訊，請參閱 [如何：手動產生用戶端資料服務類別](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。

DataSvcUtil.exe 工具會安裝在 .NET Framework 目錄中。 在許多情況下，這是位於 *c:\windows\microsoft.net\framework\v4.0 加入*中。 若為64位的系統，這會位於 *C:\Windows\Microsoft.NET\Framework64\v4.0*。 您也可以從 Visual Studio 的開發人員命令提示字元存取 DataSvcUtil.exe 工具。

## <a name="syntax"></a>語法

```console
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
|`/version:`[1.0&#124;2.0]|指定最高接受的 OData 版本。 版本是根據 `DataServiceVersion` 傳回的資料服務中繼資料中 DataService 元素的屬性來決定。 如需詳細資訊，請參閱 [資料服務版本控制](data-service-versioning-wcf-data-services.md)。 當您指定 `/dataservicecollection` 參數時，您也必須指定 `/version:2.0` 來啟用資料系結。|

## <a name="see-also"></a>另請參閱

- [產生資料服務用戶端程式庫](generating-the-data-service-client-library-wcf-data-services.md)
- [作法：新增資料服務參考](how-to-add-a-data-service-reference-wcf-data-services.md)
