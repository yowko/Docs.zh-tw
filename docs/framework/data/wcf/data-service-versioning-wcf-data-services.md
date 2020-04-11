---
title: 資料服務版本控制 (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- versioning, WCF Data Services
- versioning [WCF Data Services]
- WCF Data Services, versioning
ms.assetid: e3e899cc-7f25-4f67-958f-063f01f79766
ms.openlocfilehash: f82ab4c98e724bbed658a6c77de9c5a5d5c3390f
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121531"
---
# <a name="data-service-versioning-wcf-data-services"></a>資料服務版本控制 (WCF Data Services)
開放資料協定 (OData) 使您能夠建立數據服務,以便用戶端可以使用基於資料模型的 URI 將數據作為資源存取數據。 OData 還支援服務操作的定義。 初始部署並在其存留期期間潛在進行數次之後，可能會因為各種原因而需要變更這些資料服務 (例如變更商務需要、資訊技術需求) 或處理其他問題。 當您針對現有的資料服務進行變更時，必須考慮是否要定義新的資料服務版本，以及如何妥善地將對於現有用戶端應用程式的影響降至最低。 本主題提供建立新資料服務版本時機和方式的指引。 它還介紹了 WCF 數據服務如何處理支援 OData 協定不同版本的用戶端和數據服務之間的交換。

## <a name="versioning-a-wcf-data-service"></a>WCF Data Services 的版本控制
 部署資料服務並取用資料之後，對於資料服務的變更便有可能造成與現有用戶端應用程式的相容性問題。 不過，由於服務的整體商務需求通常需要變更，因此您必須考慮建立新資料服務版本的時機與方式，並將對於用戶端應用程式的影響降至最低。

### <a name="data-model-changes-that-recommend-a-new-data-service-version"></a>建議新資料服務版本的資料模型變更
 考慮是否要發行新資料服務版本時，最好先了解不同種類的變更影響用戶端應用程式的方式。 對於可能要求您建立新資料服務版本之資料服務的變更可分成下列兩種類別：

- 對於服務合約的變更—其中包括服務作業的更新、對於實體集 (摘要) 存取範圍的變更、版本變更，以及對於服務行為的其他變更。

- 對於資料合約的變更—其中包括對於資料模型、摘要格式或摘要自訂的變更。

 下表詳細說明您應該考慮發行新資料服務版本的哪些變更種類：

|變更類型|需要新版本|不需要新版本|
|--------------------|----------------------------|----------------------------|
|服務作業|- 新增新參數<br />- 變更傳回類型<br />- 刪除維修操作|- 刪除現有參數<br />- 新增服務操作|
|服務行為|- 停用計數要求<br />- 關閉投影支援<br />- 增加所需的資料服務版本|- 啟用計數要求<br />- 開啟投影支援<br />- 減少所需的資料服務版本|
|實體集權限|- 限制實體設定權限<br />- 變更回應代碼 (新第一個數字值) <sup>1</sup>|- 放鬆實體設定權限<br />- 變更回應代碼(相同的第一個數字值)|
|實體屬性|- 移除現有屬性或關聯<br />- 已取消的屬性<br />- 變更現有屬性|- 新增可空屬性<sup>2</sup>|
|實體集|- 刪除實體集|- 新增衍生型態<br />- 變更基型態<br />- 新增實體集|
|摘要自訂|- 變更實體屬性對應||

 <sup>1</sup>這可能取決於用戶端應用程式對接收特定錯誤代碼的嚴格依賴程度。

 <sup>2</sup>您可以<xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A>將 該屬性`true`設置為 讓用戶端忽略數據服務發送的資料服務在用戶端上未定義的任何新屬性。 不過，進行插入時，用戶端沒有包含在 POST 要求中的屬性會設為其預設值。 若是更新，屬性中用戶端未知的任何現有資料都可能會以預設值覆寫。 在此情況下，您應該將更新當做 MERGE 要求傳送，這是預設值。 有關詳細資訊,請參閱[管理資料服務上下文](managing-the-data-service-context-wcf-data-services.md)。

### <a name="how-to-version-a-data-service"></a>如何進行資料服務的版本控制
 必要時，您可以使用更新的服務合約或資料模型建立新的服務執行個體，藉以定義新的資料服務版本。 接著，您要使用新的 URI 端點公開這個新服務，以區別舊版本。 例如：

- 舊版本：`http://services.odata.org/Northwind/v1/Northwind.svc/`

- 新版本：`http://services.odata.org/Northwind/v2/Northwind.svc/`

 升級資料服務時，用戶端也需要根據新的資料服務中繼資料進行更新，並使用新的根 URI。 如果可能，您應該維護資料服務的舊版本，以支援尚未進行升級以使用新版本的用戶端。 不再需要舊版本的資料服務時，可以將其移除。 您應該考慮在外部組態檔中維護資料服務端點 URI。

## <a name="odata-protocol-versions"></a>OData 通訊協定版本
 隨著新版本 OData 的發表,用戶端應用程式可能不使用數據服務支援的 OData 協定的相同版本。 較舊的用戶端應用程式可以存取支援較新版本 OData 的數據服務。 用戶端應用程式也可能使用較新版本的 WCF 資料服務用戶端庫,該庫支援較新版本的 OData,而不是正在存取的數據服務。

 WCF 資料服務利用 OData 提供的支援來處理此類版本控制方案。 當用戶端使用與數據服務使用不同的 OData 版本時,還支援生成和使用數據模型中數據來創建用戶端數據服務類。 有關詳細資訊,請參閱[OData:概述](https://www.odata.org/documentation/odata-version-2-0/overview/)文章中的協定版本控制部分。

### <a name="version-negotiation"></a>版本交涉
 數據服務可以配置為定義服務將使用的 OData 協定的最高版本,而不考慮用戶端請求的版本。 可以通過為數據<xref:System.Data.Services.Common.DataServiceProtocolVersion><xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A><xref:System.Data.Services.DataServiceBehavior>服務 使用的屬性指定值來執行此操作。 有關詳細資訊,請參考[設定資料服務](configuring-the-data-service-wcf-data-services.md)。

 當應用程式使用 WCF 資料服務用戶端庫存取數據服務時,庫會自動將這些標頭設置為正確的值,具體取決於 OData 的版本和應用程式中使用的功能。 默認情況下,WCF 數據服務使用支援請求的操作的最低協定版本。

 下表詳細介紹了 .NET 框架和 Silverlight 的版本,這些版本包括針對 OData 協定特定版本的 WCF 資料服務支援。

|OData 協定版本|下列版本引入的支援|
|-----------------------------------------------------------------------------------|----------------------------|
|第 1 版|- .NET 框架 3.5 服務套件 1 (SP1)<br />- 銀光版本 3|
|第 2 版|- .NET 框架 4<br />- 銀光版 4|

### <a name="metadata-versions"></a>中繼資料版本
 默認情況下,WCF 數據服務使用 CSDL 的版本 1.1 來表示數據模型。 這就是以反映提供者或自訂資料服務提供者為基礎之資料模型的情況。 但是，當資料模型使用 Entity Framework 來定義時，傳回的 CSDL 的版本會與 Entity Framework 所使用的版本相同。 CSDL 的版本由[架構元素 (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#schema-element-csdl)的命名空間決定。

 傳回之中繼資料的 `DataServices` 項目還包含 `DataServiceVersion` 屬性，該值與回應訊息中 `DataServiceVersion` 標頭的值相同。 用戶端應用程式(如 Visual Studio 中的 **『添加服務參考』** 對話方塊)使用此資訊生成用戶端數據服務類,這些類與承載資料服務的 WCF 資料服務版本正常工作。 有關詳細資訊,請參閱[OData:概述](https://www.odata.org/documentation/odata-version-2-0/overview/)文章中的協定版本控制部分。

## <a name="see-also"></a>另請參閱

- [資料服務提供者](data-services-providers-wcf-data-services.md)
- [定義 WCF 資料服務](defining-wcf-data-services.md)
